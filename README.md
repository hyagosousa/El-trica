
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
/* =========================
   FIX PRINCIPAL AQUI
========================= */

function safeGrid(){
  return { color: "rgba(255,255,255,.06)" };
}

/* =========================
   EXEMPLO DE USO CORRIGIDO
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
   HEATMAP (CORRIGIDO)
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
        grid: safeGrid()   // ✅ corrigido
      },
      y: {
        type: "linear",
        grid: safeGrid()   // ✅ corrigido
      }
    }
  }
});

/* =========================
   TIMELINE (CORRIGIDO)
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
        grid: safeGrid()   // ✅ corrigido
      },
      y: {
        grid: safeGrid(),  // ✅ corrigido
        suggestedMin: 0,
        suggestedMax: 100
      }
    }
  }
});

</script>

</body>
</html>
