<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Gestão de Serviços Elétricos - Motorhome</title>
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <style>
    body { font-family: Arial, sans-serif; margin: 20px; }
    h2 { color: #1a73e8; }
    .kanban { display: flex; gap: 15px; margin-bottom: 30px; }
    .kanban-col { flex: 1; background: #f4f4f4; padding: 10px; border-radius: 8px; min-height: 120px;}
    .card { background: #fff; border: 1px solid #ccc; margin-bottom: 10px; padding: 8px; border-radius: 4px;}
    .card.atrasado { border-color: #e53935; color: #e53935; }
    .form-row { margin-bottom: 10px; }
    label { display: block; margin-bottom: 2px; }
    input, select, textarea { width: 100%; padding: 4px; }
    .dashboard { margin-bottom: 30px; }
    button { background: #1a73e8; color: white; border: none; padding: 7px 14px; border-radius: 5px; cursor: pointer; }
    button:hover { background: #1764b5; }
  </style>
</head>
<body>
  <h2>Gestão de Serviços Elétricos - Motorhome</h2>

  <div class="dashboard">
    <b>Total de OS:</b> <span id="total-os">0</span> |
    <b>Em andamento:</b> <span id="em-andamento">0</span> |
    <b>Atrasadas:</b> <span id="atrasadas">0</span>
    <div><canvas id="chart" width="320" height="120"></canvas></div>
  </div>

  <form id="service-form">
    <h3>Nova Ordem de Serviço</h3>
    <div class="form-row"><label>Cliente:</label><input type="text" id="cliente" required></div>
    <div class="form-row"><label>Motorhome:</label><input type="text" id="veiculo" required></div>
    <div class="form-row"><label>Serviço:</label>
      <select id="servico" required>
        <option value="">Selecione</option>
        <option>Instalação de Placa Solar</option>
        <option>Revisão de Fiação</option>
        <option>Troca de Bateria</option>
        <option>Outro</option>
      </select>
    </div>
    <div class="form-row"><label>Data de Entrega Prevista:</label><input type="date" id="dataEntrega" required></div>
    <div class="form-row"><label>Técnico:</label><input type="text" id="tecnico" required></div>
    <div class="form-row"><label>Observações:</label><textarea id="obs"></textarea></div>
    <button type="submit">Adicionar OS</button>
  </form>

  <br><button onclick="exportCSV()">Exportar Relatório (CSV)</button>

  <h3>Quadro Kanban</h3>
  <div class="kanban">
    <div class="kanban-col" id="afazer"><b>A Fazer</b></div>
    <div class="kanban-col" id="emexecucao"><b>Em Execução</b></div>
    <div class="kanban-col" id="concluido"><b>Concluído</b></div>
  </div>

  <script>
    // Armazena OS no localStorage
    function getOS() {
      return JSON.parse(localStorage.getItem("os_motorhome") || "[]");
    }
    function setOS(os) {
      localStorage.setItem("os_motorhome", JSON.stringify(os));
    }

    // Adiciona nova OS
    document.getElementById("service-form").onsubmit = function(e){
      e.preventDefault();
      let os = getOS();
      os.push({
        id: Date.now(),
        cliente: cliente.value,
        veiculo: veiculo.value,
        servico: servico.value,
        dataEntrega: dataEntrega.value,
        tecnico: tecnico.value,
        obs: obs.value,
        status: "A Fazer",
        dataCriacao: new Date().toISOString()
      });
      setOS(os);
      this.reset();
      render();
    };

    // Renderiza dashboard, kanban, gráfico
    function render(){
      let os = getOS();
      // Indicadores
      document.getElementById("total-os").textContent = os.length;
      document.getElementById("em-andamento").textContent = os.filter(x=>x.status!=="Concluído").length;
      // Atrasadas: não concluídas e dataEntrega < hoje
      let hj = new Date().toISOString().slice(0,10);
      let atrasadas = os.filter(x=>x.status!=="Concluído" && x.dataEntrega < hj).length;
      document.getElementById("atrasadas").textContent = atrasadas;

      // Kanban
      ["afazer","emexecucao","concluido"].forEach(col=>document.getElementById(col).innerHTML = `<b>${{
        afazer:"A Fazer",emexecucao:"Em Execução",concluido:"Concluído"
      }[col]}</b>`);
      os.forEach(item=>{
        let col = item.status==="A Fazer" ? "afazer" : item.status==="Em Execução" ? "emexecucao" : "concluido";
        let atrasado = (item.status!=="Concluído" && item.dataEntrega < hj) ? "atrasado" : "";
        let card = `<div class="card ${atrasado}">
          <b>${item.servico}</b><br>
          <small>${item.cliente} - ${item.veiculo}<br>
          Técnico: ${item.tecnico}<br>
          Entrega: ${item.dataEntrega}${atrasado ? " <b>(Atrasado)</b>" : ""}<br>
          Status: ${item.status}</small>
          <br>
          <button onclick="mudaStatus(${item.id})">Mover</button>
          ${item.status!=="Concluído" ? `<button onclick="concluirOS(${item.id})">Concluir</button>` : ""}
        </div>`;
        document.getElementById(col).innerHTML += card;
      });

      // Dashboard gráfico (exemplo: total por status)
      let ctx = document.getElementById("chart").getContext('2d');
      ctx.clearRect(0,0,320,120);
      let counts = [
        os.filter(x=>x.status==="A Fazer").length,
        os.filter(x=>x.status==="Em Execução").length,
        os.filter(x=>x.status==="Concluído").length
      ];
      let colors = ["#757575","#1a73e8","#43a047"];
      counts.forEach((v,i)=>{
        ctx.fillStyle = colors[i];
        ctx.fillRect(30+90*i, 120-v*20, 40, v*20);
        ctx.fillStyle="#333";
        ctx.fillText(["A Fazer","Exec.","Concl." ][i]+" ("+v+")",30+90*i,115);
      });
    }

    // Muda Status (A Fazer > Em Execução > Concluído)
    function mudaStatus(id){
      let os = getOS();
      let idx = os.findIndex(x=>x.id===id);
      if(os[idx].status==="A Fazer") os[idx].status = "Em Execução";
      else if(os[idx].status==="Em Execução") os[idx].status = "Concluído";
      setOS(os); render();
    }
    function concluirOS(id){
      let os = getOS();
      let idx = os.findIndex(x=>x.id===id);
      os[idx].status = "Concluído";
      setOS(os); render();
    }

    // Exportar CSV
    function exportCSV(){
      let os = getOS();
      let csv = "Cliente,Veículo,Serviço,Data Entrega,Técnico,Status,Observações\n";
      os.forEach(item=>{
        csv += [
          item.cliente, item.veiculo, item.servico, item.dataEntrega,
          item.tecnico, item.status, item.obs.replace(/\n/g," ")
        ].map(v=>`"${v}"`).join(",")+"\n";
      });
      let blob = new Blob([csv], {type:"text/csv"});
      let url = URL.createObjectURL(blob);
      let a = document.createElement("a");
      a.href = url;
      a.download = "relatorio_motorhome.csv";
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
    }

    render();
  </script>
</body>
</html>
