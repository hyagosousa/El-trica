<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Dashboard Controle Processo — Fase Elétrica</title>

  <style>
    :root{
      --bg:#0b1220;
      --card:#121c33;
      --muted:#8ea0c2;
      --text:#e7efff;
      --line:rgba(255,255,255,.08);
      --good:#2ecc71;
      --bad:#e74c3c;
      --na:#f1c40f;
      --info:#4aa3ff;
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --radius: 14px;
    }

    body{
      margin:0;
      font-family: system-ui;
      background: radial-gradient(1200px 600px at 20% 0%, #1b2a55 0%, var(--bg) 45%, #070b14 100%);
      color:var(--text);
    }

    canvas{width:100% !important;height:290px !important;}
    .smallCanvas canvas{height:240px !important;}
  </style>
</head>

<body>

<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>

<script>
function safeGrid(){
  return { color: "rgba(255,255,255,.06)" };
}

/* =========================
   GRÁFICO BARRA
========================= */

const ctx = document.createElement("canvas");
document.body.appendChild(ctx);

new Chart(ctx, {
  type: "bar",
  data: {
    labels: ["A", "B", "C"],
    datasets: [{
      label: "Teste",
      data: [10, 20, 30],
      backgroundColor: "rgba(74,163,255,.7)"
    }]
  },
  options: {
    scales: {
      x: {
        ticks: { color: "#cfe0ff" },
        grid: safeGrid()
      },
      y: {
        ticks: { color: "#cfe0ff" },
        grid: safeGrid()
      }
    }
  }
});

/* =========================
   HEATMAP
========================= */

const heatCanvas = document.createElement("canvas");
document.body.appendChild(heatCanvas);

new Chart(heatCanvas, {
  type: "scatter",
  data: {
    datasets: [{
      label: "Heatmap",
      data: [
        {x:0,y:0},
        {x:1,y:1}
      ],
      backgroundColor: "rgba(46,204,113,.6)",
      pointRadius: 10
    }]
  },
  options: {
    scales: {
      x: {
        type: "linear",
        grid: safeGrid()
      },
      y: {
        type: "linear",
        grid: safeGrid()
      }
    }
  }
});

/* =========================
   TIMELINE
========================= */

const lineCanvas = document.createElement("canvas");
document.body.appendChild(lineCanvas);

new Chart(lineCanvas, {
  type: "line",
  data: {
    labels: ["Semana 1","Semana 2","Semana 3"],
    datasets: [{
      label: "% SIM",
      data: [40, 60, 80],
      borderColor: "#4aa3ff",
      fill: true
    }]
  },
  options: {
    scales: {
      x: {
        grid: safeGrid()
      },
      y: {
        grid: safeGrid(),
        suggestedMin: 0,
        suggestedMax: 100
      }
    }
  }
});
</script>

<!-- =========================
     MÓDULO MANUTENÇÕES
========================= -->

<div style="
  margin:30px auto;
  max-width:1100px;
  background:var(--card);
  border:1px solid var(--line);
  border-radius:var(--radius);
  box-shadow:var(--shadow);
  padding:20px;
">

  <h2 style="margin:0 0 15px 0; font-size:18px;">
    🚐 Controle de Manutenções de Veículos
  </h2>

  <div style="display:grid;grid-template-columns:repeat(5,1fr);gap:10px;">

    <input id="veiculo" placeholder="Veículo"
      style="padding:10px;border-radius:10px;border:1px solid var(--line);background:#0f1930;color:var(--text);">

    <input id="entrada" type="date"
      style="padding:10px;border-radius:10px;border:1px solid var(--line);background:#0f1930;color:var(--text);">

    <input id="saida" type="date"
      style="padding:10px;border-radius:10px;border:1px solid var(--line);background:#0f1930;color:var(--text);">

    <input id="responsavel" placeholder="Responsável"
      style="padding:10px;border-radius:10px;border:1px solid var(--line);background:#0f1930;color:var(--text);">

    <select id="status"
      style="padding:10px;border-radius:10px;border:1px solid var(--line);background:#0f1930;color:var(--text);">

      <option>Em andamento</option>
      <option>Aguardando peça</option>
      <option>Finalizado</option>
    </select>

  </div>

  <button onclick="addManutencao()"
    style="
      margin-top:12px;
      padding:10px 15px;
      border-radius:10px;
      border:none;
      background:var(--info);
      color:white;
      cursor:pointer;
      font-weight:600;
    ">
    + Adicionar Manutenção
  </button>

  <div style="margin-top:20px;overflow:auto;">
    <table style="width:100%;border-collapse:collapse;min-width:800px;">
      <thead>
        <tr style="text-align:left;color:var(--muted);border-bottom:1px solid var(--line);">
          <th>Veículo</th>
          <th>Entrada</th>
          <th>Saída Prevista</th>
          <th>Responsável</th>
          <th>Status</th>
        </tr>
      </thead>

      <tbody id="tabelaManutencao"></tbody>
    </table>
  </div>

</div>

<script>
function addManutencao(){

  const veiculo = document.getElementById("veiculo").value;
  const entrada = document.getElementById("entrada").value;
  const saida = document.getElementById("saida").value;
  const responsavel = document.getElementById("responsavel").value;
  const status = document.getElementById("status").value;

  if(!veiculo || !entrada || !responsavel){
    alert("Preencha Veículo, Entrada e Responsável");
    return;
  }

  let cor = "#f1c40f";
  if(status === "Finalizado") cor = "#2ecc71";
  if(status === "Aguardando peça") cor = "#e74c3c";

  const row = `
    <tr style="border-bottom:1px solid var(--line);">
      <td>${veiculo}</td>
      <td>${entrada}</td>
      <td>${saida || "-"}</td>
      <td>${responsavel}</td>
      <td style="color:${cor};font-weight:600;">${status}</td>
    </tr>
  `;

  document.getElementById("tabelaManutencao").innerHTML += row;

  document.getElementById("veiculo").value = "";
  document.getElementById("entrada").value = "";
  document.getElementById("saida").value = "";
  document.getElementById("responsavel").value = "";
}
</script>

</body>
</html>
