<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Sistema MES Simplificado — Produção Elétrica</title>

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

    header{
      padding:18px;
      border-bottom:1px solid var(--line);
      position:sticky;
      top:0;
      backdrop-filter: blur(10px);
    }

    h1{font-size:18px;margin:0;}
    .sub{font-size:12px;color:var(--muted);margin-top:6px;}
  </style>
</head>

<body>

<header>
  <h1>🏭 Sistema MES Simplificado — Monitoramento de Produção Elétrica</h1>
  <div class="sub">
    Controle de execução de tarefas, rastreabilidade por responsável técnico e análise de eficiência operacional.
  </div>
</header>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<script>
/* =========================
   PADRÃO INDUSTRIAL
========================= */

const STATUS = {
  CONCLUIDO: "CONCLUIDO",
  NAO_CONCLUIDO: "NAO_CONCLUIDO",
  NAO_APLICAVEL: "NAO_APLICAVEL"
};

/* conversor visual (não quebra sua base antiga) */
function statusLabel(st){
  if(st==="SIM") return "✔ Concluído";
  if(st==="NAO") return "❌ Não Concluído";
  if(st==="NA") return "⚪ Não Aplicável";
  return st;
}

/* =========================
   TÍTULOS KPI (INDUSTRIAL)
========================= */

const KPIS = {
  eficiencia: "Eficiência Operacional (%)",
  retrabalho: "Taxa de Retrabalho (%)",
  atraso: "Desvio Médio de Prazo (dias)",
  backlog: "Backlog de Produção (Pendências)",
  dentroPrazo: "Aderência ao Prazo (%)",
  atrasoCritico: "Índice de Atraso Crítico (%)"
};

/* =========================
   EXEMPLO SIMPLES (MANTIDO)
========================= */

const ctx = document.createElement("canvas");
document.body.appendChild(ctx);

new Chart(ctx, {
  type:"bar",
  data:{
    labels:["Linha A","Linha B","Linha C"],
    datasets:[{
      label:"Eficiência Operacional",
      data:[78,85,92],
      backgroundColor:"rgba(74,163,255,.7)"
    }]
  },
  options:{
    plugins:{
      title:{
        display:true,
        text:"📊 Eficiência Operacional por Linha de Produção"
      }
    },
    scales:{
      x:{grid:{color:"rgba(255,255,255,.06)"}},
      y:{grid:{color:"rgba(255,255,255,.06)"}, suggestedMax:100}
    }
  }
});

</script>

</body>
</html>
