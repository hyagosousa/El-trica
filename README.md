
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">

<!-- Begin Jekyll SEO tag v2.8.0 -->
<title>El-trica</title>
<meta name="generator" content="Jekyll v3.10.0" />
<meta property="og:title" content="El-trica" />
<meta property="og:locale" content="en_US" />
<link rel="canonical" href="https://hyagosousa.github.io/El-trica/" />
<meta property="og:url" content="https://hyagosousa.github.io/El-trica/" />
<meta property="og:site_name" content="El-trica" />
<meta property="og:type" content="website" />
<meta name="twitter:card" content="summary" />
<meta property="twitter:title" content="El-trica" />
<script type="application/ld+json">
{"@context":"https://schema.org","@type":"WebSite","headline":"El-trica","name":"El-trica","url":"https://hyagosousa.github.io/El-trica/"}</script>
<!-- End Jekyll SEO tag -->

    <link rel="stylesheet" href="/El-trica/assets/css/style.css?v=a469a5d6f81326aa4bafcf8fa15ed9c4688e8ba1">
    <!-- start custom head snippets, customize with your own _includes/head-custom.html file -->

<!-- Setup Google Analytics -->



<!-- You can set your favicon here -->
<!-- link rel="shortcut icon" type="image/x-icon" href="/El-trica/favicon.ico" -->

<!-- end custom head snippets -->

  </head>
  <body>
    <div class="container-lg px-3 my-5 markdown-body">
      
      <h1><a href="https://hyagosousa.github.io/El-trica/">El-trica</a></h1>
      

      
<p>&lt;!doctype html&gt;</p>
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


      
    </div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/anchor-js/4.1.0/anchor.min.js" integrity="sha256-lZaRhKri35AyJSypXXs4o6OPFTbTmUoltBbDCbdzegg=" crossorigin="anonymous"></script>
    <script>anchors.add();</script>
  </body>
</html>
