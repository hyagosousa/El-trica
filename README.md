<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dashboard Motorhomes - Globe</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #0b0f1a;
  color: #fff;
}

/* HEADER */
header {
  padding: 20px;
  background: #111a2e;
  text-align: center;
  font-size: 20px;
  font-weight: bold;
  letter-spacing: 1px;
}

/* GRID */
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15px;
  padding: 15px;
}

.card {
  background: #121c33;
  padding: 15px;
  border-radius: 10px;
}

/* KPIs */
.kpi {
  display: flex;
  justify-content: space-between;
  margin: 5px 0;
  padding: 8px;
  background: #0f172a;
  border-radius: 6px;
}

/* OS LIST */
.os {
  padding: 10px;
  margin: 8px 0;
  border-radius: 8px;
  background: #0f172a;
  transition: 0.3s;
}

.os strong {
  display: block;
}

/* ALERTA AMARELO */
.warning {
  border: 2px solid #ffcc00;
  color: #ffcc00;
  animation: blinkWarn 1.2s infinite;
}

/* ALERTA VERMELHO */
.danger {
  background: #3a0d0d;
  border: 2px solid red;
  color: #ff3b3b;
  animation: blinkDanger 0.8s infinite;
  font-weight: bold;
}

@keyframes blinkDanger {
  0% {opacity: 1;}
  50% {opacity: 0.3;}
  100% {opacity: 1;}
}

@keyframes blinkWarn {
  0% {border-color: #ffcc00;}
  50% {border-color: transparent;}
  100% {border-color: #ffcc00;}
}

/* STATUS TAGS */
.status {
  font-size: 12px;
  padding: 3px 8px;
  border-radius: 5px;
  display: inline-block;
  margin-top: 5px;
}

.em-andamento { background: #1e3a8a; }
.executado { background: #166534; }
.aguardando { background: #92400e; }
.parado { background: #374151; }
.concluido { background: #065f46; }

/* CHART */
canvas {
  background: #0f172a;
  padding: 10px;
  border-radius: 10px;
}
</style>
</head>

<body>

<header>
DASHBOARD MOTORHOMES • GLOBE SYSTEM
</header>

<div class="container">

<!-- KPIs -->
<div class="card">
<h3>Indicadores</h3>

<div class="kpi"><span>OS Abertas</span><strong>12</strong></div>
<div class="kpi"><span>Em Andamento</span><strong>6</strong></div>
<div class="kpi"><span>Concluídas</span><strong>9</strong></div>
<div class="kpi"><span>Atrasadas</span><strong id="atrasadas">0</strong></div>

</div>

<!-- CHART -->
<div class="card">
<h3>Status Geral</h3>
<canvas id="chartStatus"></canvas>
</div>

<!-- OS LIST -->
<div class="card" style="grid-column: span 2;">
<h3>Ordens de Serviço</h3>
<div id="osList"></div>
</div>

</div>

<script>
// ========================
// DADOS EXEMPLO
// ========================
const osData = [
  {id:"MH-121", cliente:"Carlos", status:"em andamento", entrega:"2026-06-20"},
  {id:"MH-125", cliente:"João", status:"aguardando", entrega:"2026-06-26"},
  {id:"MH-130", cliente:"Pedro", status:"executado", entrega:"2026-06-30"},
  {id:"MH-118", cliente:"Lucas", status:"em andamento", entrega:"2026-06-23"},
  {id:"MH-140", cliente:"Rafael", status:"parado", entrega:"2026-06-22"}
];

// ========================
// CALCULO STATUS PRAZO
// ========================
function getAlert(entrega){
  const hoje = new Date();
  const data = new Date(entrega);
  const diff = (data - hoje) / (1000*60*60*24);

  if(diff < 0) return "danger";
  if(diff <= 3) return "warning";
  return "";
}

// ========================
// RENDER OS
// ========================
function renderOS(){

  const container = document.getElementById("osList");
  container.innerHTML = "";

  let atrasadas = 0;

  // ordena prioridade (atrasados primeiro)
  osData.sort((a,b)=> new Date(a.entrega) - new Date(b.entrega));

  osData.forEach(os => {

    const alertClass = getAlert(os.entrega);

    if(alertClass === "danger") atrasadas++;

    const div = document.createElement("div");
    div.className = "os " + alertClass;

    div.innerHTML = `
      <strong>
        ${alertClass === "danger" ? "🚨" : alertClass === "warning" ? "⚠" : ""}
        ${os.id} • ${os.cliente}
      </strong>

      <div>Entrega: ${os.entrega}</div>

      <span class="status ${os.status.replace(" ","-")}">
        ${os.status.toUpperCase()}
      </span>
    `;

    container.appendChild(div);
  });

  document.getElementById("atrasadas").innerText = atrasadas;
}

// ========================
// GRAFICO
// ========================
function chart(){
const ctx = document.getElementById('chartStatus');

new Chart(ctx, {
  type: 'pie',
  data: {
    labels: ['Concluído', 'Em andamento', 'Aguardando', 'Parado'],
    datasets: [{
      data: [40, 30, 20, 10],
      backgroundColor: ['#16a34a','#2563eb','#f59e0b','#6b7280']
    }]
  }
});
}

renderOS();
chart();

</script>

</body>
</html>
