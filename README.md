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
      --purple:#9b59b6;
      --orange:#f39c12;
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --radius: 14px;
    }
    body{
      margin:0;
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, sans-serif;
      background: radial-gradient(1200px 600px at 20% 0%, #1b2a55 0%, var(--bg) 45%, #070b14 100%);
      color:var(--text);
    }
    header{
      padding:22px 18px;
      border-bottom:1px solid var(--line);
      background: linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,0));
      position: sticky;
      top:0;
      z-index: 10;
      backdrop-filter: blur(10px);
    }
    .wrap{max-width: 1200px; margin:0 auto;}
    h1{font-size:18px; margin:0 0 8px 0; letter-spacing:.3px;}
    .sub{color:var(--muted); font-size:12.5px; margin:0;}
    .grid{
      display:grid; grid-template-columns: 1fr;
      gap:14px;
      padding: 14px 18px 28px;
    }
    @media(min-width: 980px){
      .grid{
        grid-template-columns: 360px 1fr;
        align-items:start;
      }
    }
    .panel{
      background: rgba(18,28,51,.82);
      border: 1px solid var(--line);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      overflow:hidden;
    }
    .panel .hd{
      padding:14px 14px 10px;
      border-bottom:1px solid var(--line);
      display:flex; align-items:center; justify-content:space-between;
      gap:10px;
    }
    .panel .hd b{font-size:13.5px;}
    .panel .bd{padding:14px;}
    .row{display:flex; gap:10px; flex-wrap:wrap;}
    .field{display:flex; flex-direction:column; gap:6px; margin-bottom:12px; width:100%;}
    label{font-size:12px; color:var(--muted);}
    select,input[type="date"],input[type="text"]{
      width:100%;
      padding:10px 10px;
      background:#0f1730;
      color:var(--text);
      border:1px solid var(--line);
      border-radius:10px;
      outline:none;
    }
    input[type="range"]{width:100%;}
    .btn{
      appearance:none;
      border:1px solid var(--line);
      background:#0f1730;
      color:var(--text);
      padding:10px 12px;
      border-radius: 10px;
      cursor:pointer;
      transition:.15s;
      font-weight:600;
      font-size:12.5px;
    }
    .btn:hover{transform: translateY(-1px); border-color: rgba(255,255,255,.18);}
    .btn.primary{
      background: linear-gradient(135deg, rgba(74,163,255,.25), rgba(155,89,182,.25));
      border-color: rgba(74,163,255,.35);
    }
    .btn.good{
      border-color: rgba(46,204,113,.35);
      background: rgba(46,204,113,.12);
    }
    .kpiGrid{
      display:grid;
      grid-template-columns: repeat(2, minmax(0,1fr));
      gap:10px;
    }
    @media(min-width: 560px){ .kpiGrid{grid-template-columns: repeat(4, minmax(0,1fr));} }
    .kpi{
      padding:12px;
      border:1px solid var(--line);
      border-radius: 12px;
      background: rgba(255,255,255,.03);
    }
    .kpi .v{font-size:18px; font-weight:800; letter-spacing:.2px;}
    .kpi .t{font-size:12px; color:var(--muted); margin-top:4px;}
    .legend{
      display:flex; gap:14px; flex-wrap:wrap; font-size:12px; color:var(--muted);
      margin-top:8px;
    }
    .dot{width:10px; height:10px; border-radius:50%; display:inline-block; margin-right:6px; vertical-align:middle;}
    .cards2{
      display:grid;
      grid-template-columns: 1fr;
      gap:14px;
      padding:0 18px 28px;
    }
    @media(min-width: 980px){
      .cards2{grid-template-columns: 1fr; padding:0 18px 28px;}
    }
    .chartGrid{
      display:grid;
      grid-template-columns: 1fr;
      gap:14px;
      padding:0 18px 28px;
    }
    @media(min-width: 980px){
      .chartGrid{
        grid-template-columns: 1fr 1fr;
      }
      .span2{grid-column: span 2;}
    }
    .chart{
      padding:14px;
    }
    canvas{
      width:100% !important;
      height: 290px !important;
    }
    .smallCanvas canvas{ height: 240px !important; }
    .table{
      width:100%;
      border-collapse: collapse;
      font-size:12.5px;
    }
    .table th,.table td{
      border-bottom:1px solid var(--line);
      padding:8px 6px;
      text-align:left;
      vertical-align:top;
    }
    .badge{
      display:inline-flex; align-items:center; gap:8px;
      border:1px solid var(--line);
      padding:6px 10px;
      border-radius: 999px;
      font-size:12px;
      color:var(--muted);
      background: rgba(255,255,255,.03);
    }
    .badge strong{color:var(--text);}
    .muted{color:var(--muted);}
    .pill{
      display:inline-flex; align-items:center;
      padding:5px 9px;
      border-radius:999px;
      border:1px solid var(--line);
      background: rgba(255,255,255,.03);
      font-weight:700;
      font-size:12px;
    }
    .pill.good{border-color: rgba(46,204,113,.35); color:#bff7d8; background: rgba(46,204,113,.10);}
    .pill.bad{border-color: rgba(231,76,60,.35); color:#ffd0cc; background: rgba(231,76,60,.10);}
    .pill.na{border-color: rgba(241,196,15,.35); color:#ffe9ad; background: rgba(241,196,15,.10);}
    .pill.info{border-color: rgba(74,163,255,.35); color:#d4ecff; background: rgba(74,163,255,.10);}
    .toast{
      position: fixed; right: 14px; bottom: 14px;
      background:#0f1730;
      border:1px solid var(--line);
      color:var(--text);
      padding:12px 12px;
      border-radius: 12px;
      box-shadow: var(--shadow);
      max-width: 420px;
      display:none;
      z-index:100;
    }
    .toast.show{display:block;}
  </style>
</head>
<body>
<header>
  <div class="wrap">
    <h1>⚡ Dashboard Interativo — Controle de Processo (Área Elétrica / Checklist Fase Elétrica)</h1>
    <p class="sub">Filtre por datas, carro/modelo, responsável, fase, tarefa e status. Inclui KPIs, heatmap, Pareto, histogramas e timeline.</p>
  </div>
</header>

<div class="grid wrap">
  <!-- Left filter panel -->
  <div class="panel">
    <div class="hd"><b>🎛️ Filtros & Controle</b><span class="muted" id="filterCount"></span></div>
    <div class="bd">
      <div class="field">
        <label>Modo de cálculo (conclusão considera N.A.?)</label>
        <select id="naMode">
          <option value="exclude" selected>Excluir N.A. do denominador</option>
          <option value="include">Incluir N.A. no denominador</option>
        </select>
      </div>

      <div class="field">
        <label>Data Início (Data prevista / real no registro)</label>
        <input type="date" id="fromDate"/>
      </div>
      <div class="field">
        <label>Data Fim</label>
        <input type="date" id="toDate"/>
      </div>

      <div class="field">
        <label>Carro</label>
        <select id="carFilter">
          <option value="__ALL__">Todos</option>
        </select>
      </div>

      <div class="field">
        <label>Modelo</label>
        <select id="modelFilter">
          <option value="__ALL__">Todos</option>
        </select>
      </div>

      <div class="field">
        <label>Responsável</label>
        <select id="respFilter">
          <option value="__ALL__">Todos</option>
        </select>
      </div>

      <div class="field">
        <label>Fase</label>
        <select id="phaseFilter">
          <option value="__ALL__">Todas</option>
        </select>
      </div>

      <div class="field">
        <label>Status</label>
        <select id="statusFilter">
          <option value="__ALL__">Todos (SIM/NÃO/N.A.)</option>
          <option value="SIM">SIM</option>
          <option value="NA">N.A.</option>
          <option value="NAO">NÃO</option>
        </select>
      </div>

      <div class="field">
        <label>Busca por tarefa (contém)</label>
        <input type="text" id="taskSearch" placeholder="Ex.: ESTABILIZADOR..." />
      </div>

      <div class="field">
        <label>Somente pendências (Status = NÃO)</label>
        <select id="onlyPending">
          <option value="no" selected>Não</option>
          <option value="yes">Sim</option>
        </select>
      </div>

      <div class="row">
        <button class="btn primary" id="btnApply">✅ Aplicar filtros</button>
        <button class="btn" id="btnReset">↩️ Resetar</button>
      </div>

      <hr style="border:0;border-top:1px solid var(--line);margin:14px 0;"/>

      <div class="row" style="justify-content:space-between;">
        <button class="btn good" id="btnLoadSample">✨ Usar dados de exemplo</button>
        <button class="btn" id="btnExport">⬇️ Exportar filtros (JSON)</button>
      </div>

      <div style="height:10px;"></div>

      <div class="field">
        <label>Carregar seus registros via CSV 📄</label>
        <input type="file" id="csvFile" accept=".csv,text/csv"/>
        <div class="muted" style="font-size:12px;line-height:1.35;margin-top:6px;">
          Formato esperado (header obrigatório):
          <br/>- <b>carro</b>, <b>modelo</b>, <b>fase</b>, <b>tarefa</b>, <b>responsavel</b>
          <br/>- <b>dt_prev</b>, <b>dt_real</b> (YYYY-MM-DD ou vazio)
          <br/>- <b>status</b> (SIM|NA|NAO)
        </div>
      </div>

    </div>
  </div>

  <!-- Right: main content top KPIs -->
  <div>
    <div class="panel">
      <div class="hd"><b>📌 Visão Executiva</b><span class="badge"><span class="dot" style="background:var(--info)"></span><strong id="scopeText">—</strong></span></div>
      <div class="bd">
        <div class="kpiGrid">
          <div class="kpi"><div class="v" id="kpiTotal">—</div><div class="t">Tarefas consideradas</div></div>
          <div class="kpi"><div class="v" id="kpiSim">—</div><div class="t">% SIM</div></div>
          <div class="kpi"><div class="v" id="kpiNao">—</div><div class="t">% NÃO</div></div>
          <div class="kpi"><div class="v" id="kpiNA">—</div><div class="t">% N.A.</div></div>
        </div>

        <div style="height:10px;"></div>

        <div class="kpiGrid">
          <div class="kpi">
            <div class="v" id="kpiPendencias">—</div>
            <div class="t">Qtd. pendências (NÃO)</div>
          </div>
          <div class="kpi">
            <div class="v" id="kpiAtrasoMed">—</div>
            <div class="t">Atraso mediano (dias)</div>
          </div>
          <div class="kpi">
            <div class="v" id="kpiDentro">—</div>
            <div class="t">% dentro do prazo (≤0)</div>
          </div>
          <div class="kpi">
            <div class="v" id="kpiAtrasoMaior">—</div>
            <div class="t">% atraso alto (8+ dias)</div>
          </div>
        </div>

        <div class="legend">
          <span class="pill good">SIM</span>
          <span class="pill bad">NÃO</span>
          <span class="pill na">N.A.</span>
          <span class="pill info">Atraso = dt_real - dt_prev</span>
        </div>
      </div>
    </div>

    <div style="height:14px;"></div>

    <div class="chartGrid">
      <div class="panel chart span2">
        <div class="hd">
          <b>🧭 Status por Fase (SIM/NÃO/N.A.)</b>
          <span class="muted" id="clickHint">Clique em uma barra/legenda para filtrar drill-down</span>
        </div>
        <div class="bd">
          <canvas id="chartPhaseStack"></canvas>
        </div>
      </div>

      <div class="panel chart">
        <div class="hd"><b>🔥 Top 10 tarefas com maior taxa NÃO (Pareto base)</b></div>
        <div class="bd">
          <canvas id="chartTopNao"></canvas>
        </div>
      </div>

      <div class="panel chart">
        <div class="hd"><b>📉 Pareto — quais tarefas explicam 80% das pendências</b></div>
        <div class="bd">
          <canvas id="chartPareto"></canvas>
        </div>
      </div>

      <div class="panel chart span2">
        <div class="hd"><b>🗺️ Heatmap — Tarefa × Responsável (taxa SIM)</b><span class="muted">(Mostra até 12 tarefas e 8 responsáveis pelo filtro atual)</span></div>
        <div class="bd">
          <canvas id="heatmap"></canvas>
        </div>
      </div>

      <div class="panel chart">
        <div class="hd"><b>⏱️ Histograma — distribuição de atraso (dias)</b></div>
        <div class="bd smallCanvas">
          <canvas id="histAtraso"></canvas>
        </div>
      </div>

      <div class="panel chart">
        <div class="hd"><b>🔎 Scatter — %NÃO vs Atraso mediano (por tarefa)</b></div>
        <div class="bd smallCanvas">
          <canvas id="scatterNaoVsAtraso"></canvas>
        </div>
      </div>

      <div class="panel chart span2">
        <div class="hd"><b>🗓️ Timeline — progresso por data prevista (exemplo: média de %SIM por semana)</b><span class="muted">(baseado no dt_prev quando disponível)</span></div>
        <div class="bd">
          <canvas id="timeline"></canvas>
        </div>
      </div>

      <div class="panel chart span2">
        <div class="hd">
          <b>🧾 Lista — Drill-down (tarefas com pendência ou conforme status selecionado)</b>
          <span class="muted">Clique numa linha para destacar no dashboard</span>
        </div>
        <div class="bd" style="overflow:auto; max-height:320px;">
          <table class="table" id="tableDetails">
            <thead>
              <tr>
                <th>#</th><th>Carro/Modelo</th><th>Fase</th><th>Tarefa</th>
                <th>Responsável</th><th>Status</th><th>DT Prev</th><th>DT Real</th><th>Atraso (dias)</th>
              </tr>
            </thead>
            <tbody></tbody>
          </table>
        </div>
      </div>

    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<!-- Chart.js (via CDN) -->
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
<script>
/** =========================
 *  CONFIG / DATA MODEL
 * ========================= */

const STATUS = {
  SIM: "SIM",
  NAO: "NAO",
  NA: "NA"
};

function statusColor(st){
  if(st===STATUS.SIM) return "rgba(46,204,113,.95)";
  if(st===STATUS.NAO) return "rgba(231,76,60,.95)";
  return "rgba(241,196,15,.95)";
}
function statusPillClass(st){
  if(st===STATUS.SIM) return "pill good";
  if(st===STATUS.NAO) return "pill bad";
  return "pill na";
}
function safeDate(d){
  if(!d) return null;
  const t = Date.parse(d);
  if(Number.isNaN(t)) return null;
  return new Date(t);
}
function daysDiff(dtReal, dtPrev){
  const a = safeDate(dtReal), b = safeDate(dtPrev);
  if(!a || !b) return null;
  const ms = a - b;
  return Math.round(ms / (1000*60*60*24));
}
function fmtDate(d){
  if(!d) return "—";
  return d;
}
function median(arr){
  const x = arr.filter(v => typeof v==="number" && Number.isFinite(v)).sort((a,b)=>a-b);
  if(x.length===0) return null;
  const mid = Math.floor(x.length/2);
  return x.length%2 ? x[mid] : (x[mid-1]+x[mid])/2;
}
function quantile(arr,q){
  const x = arr.filter(v => typeof v==="number" && Number.isFinite(v)).sort((a,b)=>a-b);
  if(x.length===0) return null;
  const pos = (x.length-1)*q;
  const base = Math.floor(pos);
  const rest = pos-base;
  if(x[base+1]!==undefined) return x[base] + rest*(x[base+1]-x[base]);
  return x[base];
}

/** Checklist items extracted from the PDF template */
const TASKS = [
  {fase:"FASE 1 PASSAGEM DE CABOS C.A.", tarefas:[
    "CIRCUITO ILUMINACAO FASE/FASE - AMARELO/CINZA 2,5MM",
    "CIRCUITO TOMADAS FASE/FASE/TERRA - AZUL/BRANCO/VERDE 2,5MM"
  ]},
  {fase:"FASE 1 PASSAGEM DE CABOS C.C.", tarefas:[
    "CIRCUITO ILUMINACAO - PRETO/VERMELHO 2,5MM",
    "CABO AQUECEDOR DE PASSAGEM PP 4X1 DUPLA ISOLACAO",
    "FIO PLACA SOLAR DO TETO ATE A CENTRAL 6MM",
    "FIO AR CONDICIONADO CONFORME MANUAL E DIMENSIONAMENTO",
    "FIACAO TOLDO/ESCADA PRETO/VERMELHO 2,5MM",
    "FIACAO TOMADA 12V BASE BANCO MOTORISTA PRETO/VERMELHO 4,0MM",
    "FIACAO GELADEIRA PRETO/VERMELHO 6MM",
    "FIACAO LED PIA (QUANDO APLICAVEL) PRETO/VERMELHO 2,5MM",
    "FIACAO MOTOR SLIDE-OUT MOTOR ATE CENTRAL PRETO/VERMELHO 6MM",
    "FIACAO VALVULAS DETRITOS OU SERVIDA (QUANDO APLICAVEL) PP 2X1",
    "FIACAO BOIAS AGUA LIMPA/SUJA/DETRITOS PP 2X0,75",
    "ESTABILIZADOR ENTRADA 3 CABOS AZUL/BRANCO/VERDE 2,5MM",
    "ESTABILIZADOR SAIDA 2 CABOS AZUL/BRANCO 2,5MM",
    "CIRCUITO ILUMINACAO E TOMADA PARA SLIDE-OUT 7 CORES 2,5MM",
    "CABO TOMADA EXTERNA PP 3X4MM",
    "CHICOTE ELETRICA AUTOMOTIVA PP 0,5 VIGIAS LATERAIS, DIANTEIROS E TRASEIROS"
  ]},
  {fase:"FASE 1 CABOS DO SISTEMA DE BATERIAS", tarefas:[
    "CABO GERENCIADOR BATERIA CONFORME POTENCIA E DIMENSIONAMENTO; FIO 2,5MM VERMELHO",
    "CABOS ENTRE BATERIAS E BARRAMENTO NA CENTRAL (DIMENSIONADO PELAS CARGAS TOTAIS)",
    "CABO REDE DO PAINEL ATE A CENTRAL CAT6",
    "INTERRUPTOR USINA CABO 2,5MM FASE/FASE AZUL",
    "CABO BOMBA AGUA LIMPA ALIMENTACAO BOTAO 6MM PRETO/VERMELHO",
    "CABO 6MM VERMELHO 1 POR CADA BOMBA",
    "CABO INVERSOR PP 0,75 BOTAO"
  ]},
  {fase:"FASE 2 - LIGACOES", tarefas:[
    "LIGACAO TOMADAS 220V E 12V",
    "LIGACAO LAMPADAS E LEDS",
    "LIGACAO LUZ EXTERNA (ABAIXO DO TOLDO)",
    "LIGACAO ESCADA",
    "LIGACAO TOLDO",
    "LIGACAO SLIDE-OUT",
    "LIGACAO ESTABILIZADOR",
    "LIGACAO CLARA BOIA (SENSOR NIVEL)",
    "LIGACAO AR CONDICIONADO",
    "LIGACAO PLACA AQUECEDOR DE PASSAGEM",
    "LIGACAO LED PIA",
    "LIGACAO ILUMINACAO (LEITURA QUANDO APLICAVEL)"
  ]},
  {fase:"FASE 3 CENTRAL ELETRO-ELETRONICA", tarefas:[
    "CENTRAL ELETRO-ELETRONICA: ORGANIZAR E ROTEAR TODOS OS CABOS",
    "FIXACAO DOS EQUIPAMENTOS: ANTECIPAR O TRAJETO DO CABO E FLUXO DE AR",
    "LIGACAO DA USINA: CABO CONFORME POTENCIA DO EQUIPAMENTO",
    "1A LIGACAO DO ESTABILIZADOR DE TENSAO",
    "COLOCAR CANALETAS E PASSA-FIOS",
    "LIGACAO DAS BATERIAS: FABRICACAO E LIGACAO DO BARRAMENTO CC",
    "LIGACAO DO CARREGADOR DCDC AO BARRAMENTO CC",
    "LIGAR CONTROLADOR SOLAR",
    "LIGAR CHAVE GERAL",
    "LIGAR BLOCO DE FUSIVEL",
    "LIGAR INVERSOR",
    "MONTAR QUADRO DE ENERGIA (QBC)",
    "LIGACAO DO DETECTOR DE GAS (CONFORME PROJETO)",
    "LIGACAO DE BANCO ELETRICO (QUANDO APLICAVEL)"
  ]},
  {fase:"FASE 3 PAINEL DE COMANDO", tarefas:[
    "INSTALAR BOTOES DAS BOMBAS",
    "INSTALAR BOTAO DO INVERSOR",
    "INSTALAR BOTAO DO CARREGADOR",
    "INSTALAR PAINEL NIVEL DE AGUA",
    "CONFERIR SISTEMA GERAL (FIM)"
  ]}
];

/** Expand task list to map for validations */
const ALL_TASKS = TASKS.flatMap(g => g.tarefas.map(t => ({fase:g.fase, tarefa:t})));

/** Data record:
 * { carro, modelo, fase, tarefa, responsavel, dt_prev, dt_real, status }
 */
let data = [];

function seedData(){
  // Deterministic-ish sample dataset
  const carros = ["GLOBE-01","GLOBE-02","GLOBE-03","GLOBE-04","GLOBE-05"];
  const modelos = ["ELETRO-GL","ELETRO-GL","ELETRO-X","ELETRO-X","ELETRO-GL"];
  const responsaveis = ["Equipe A","Equipe B","Equipe C","Sergio","Marcos"];
  const fases = TASKS.map(x=>x.fase);

  // generate sparse entries for performance
  const start = new Date("2026-01-10T00:00:00Z");
  const rand = (min,max)=> Math.random()*(max-min)+min;

  const recs = [];
  for(let ci=0; ci<carros.length; ci++){
    const carro = carros[ci];
    const modelo = modelos[ci];
    const baseIndex = ci*3;
    // Choose a subset of tasks per car to keep sample manageable:
    const pickCount = 55 + (ci%2)*10;
    const chosen = new Set();
    while(chosen.size < pickCount){
      const idx = Math.floor(rand(0, ALL_TASKS.length));
      chosen.add(idx);
    }
    for(const idx of chosen){
      const {fase,tarefa} = ALL_TASKS[idx];
      const responsavel = responsaveis[Math.floor(rand(0,responsaveis.length))];
      const dtPrevDate = new Date(start.getTime() + (baseIndex + Math.floor(rand(0,22)))*24*3600*1000);
      const dtPrev = dtPrevDate.toISOString().slice(0,10);
      // status probabilities influenced by phase
      let pNao=0.18, pNa=0.08;
      if(fase.includes("FASE 3")) { pNao=0.22; pNa=0.05; }
      if(fase.includes("PASSAGEM")) { pNao=0.15; pNa=0.10; }
      const r = Math.random();
      let status = STATUS.SIM;
      if(r < pNao) status = STATUS.NAO;
      else if(r < pNao + pNa) status = STATUS.NA;

      let dtReal = "";
      if(status===STATUS.NAO){
        const atraso = Math.round(rand(2,12));
        const dtRealDate = new Date(dtPrevDate.getTime() + atraso*24*3600*1000);
        dtReal = dtRealDate.toISOString().slice(0,10);
      } else if(status===STATUS.SIM){
        const atraso = Math.round(rand(-2,3)); // can be on time or early/late a bit
        const dtRealDate = new Date(dtPrevDate.getTime() + atraso*24*3600*1000);
        dtReal = dtRealDate.toISOString().slice(0,10);
      } else {
        // NA no data real typically
        dtReal = "";
      }

      recs.push({
        carro, modelo, fase, tarefa, responsavel, dt_prev: dtPrev, dt_real: dtReal, status
      });
    }
  }
  data = recs;
}

/** =========================
 *  CSV LOADER
 * ========================= */
function parseCSV(text){
  // Minimal CSV parser (supports quoted fields)
  const rows = [];
  let i=0, cur="", inQ=false, row=[];
  while(i<text.length){
    const c = text[i];
    if(c === '"' ){
      if(inQ && text[i+1] === '"'){ cur+='"'; i+=2; continue; }
      inQ = !inQ; i++; continue;
    }
    if(!inQ && (c===',')){
      row.push(cur); cur=""; i++; continue;
    }
    if(!inQ && (c==='\n')){
      row.push(cur); cur=""; i++;
      if(row.some(v=>String(v).trim()!=="")) rows.push(row);
      row=[]; continue;
    }
    if(c==='\r'){ i++; continue; }
    cur+=c; i++;
  }
  if(cur.length || row.length) { row.push(cur); rows.push(row); }

  if(rows.length < 2) return {header:null, rows:[]};
  const header = rows[0].map(h=>String(h).trim().toLowerCase());
  const out = [];
  for(let r=1; r<rows.length; r++){
    const obj = {};
    const cols = rows[r];
    for(let c=0; c<header.length; c++){
      obj[header[c]] = (cols[c] ?? "").trim();
    }
    out.push(obj);
  }
  return {header, rows: out};
}

async function loadCSVFile(file){
  const txt = await file.text();
  const {header, rows} = parseCSV(txt);
  if(!header){
    toast("CSV inválido ou vazio.");
    return;
  }
  const required = ["carro","modelo","fase","tarefa","responsavel","dt_prev","dt_real","status"];
  const missing = required.filter(k => !header.includes(k));
  if(missing.length){
    toast("CSV não tem as colunas obrigatórias: " + missing.join(", "));
    return;
  }
  const mapped = rows.map(r => ({
    carro: r["carro"] || "",
    modelo: r["modelo"] || "",
    fase: r["fase"] || "",
    tarefa: r["tarefa"] || "",
    responsavel: r["responsavel"] || "",
    dt_prev: r["dt_prev"] || "",
    dt_real: r["dt_real"] || "",
    status: (r["status"] || "").toUpperCase() // SIM|NA|NAO
  })).filter(x => x.carro && x.fase && x.tarefa && x.status);

  // Normalize status values
  data = mapped.map(x => {
    let st = x.status;
    if(st === "N.A." || st==="N.A" || st==="NA." || st==="NA") st = STATUS.NA;
    if(st === "NÃO" || st==="NAO" || st==="NAO ") st = STATUS.NAO;
    if(st === "SIM") st = STATUS.SIM;
    return {...x, status: st};
  });

  toast(`CSV carregado: ${data.length} registros.`);
  rebuildFilters();
  applyAndRender();
}

/** =========================
 *  FILTERS
 * ========================= */
const $ = (id)=>document.getElementById(id);

function getFilterState(){
  const fromDate = $("fromDate").value;
  const toDate = $("toDate").value;
  const carFilter = $("carFilter").value;
  const modelFilter = $("modelFilter").value;
  const respFilter = $("respFilter").value;
  const phaseFilter = $("phaseFilter").value;
  const statusFilter = $("statusFilter").value;
  const taskSearch = $("taskSearch").value.trim().toLowerCase();
  const onlyPending = $("onlyPending").value === "yes";
  const naMode = $("naMode").value; // exclude/include
  return {fromDate,toDate,carFilter,modelFilter,respFilter,phaseFilter,statusFilter,taskSearch,onlyPending,naMode};
}

function inDateRange(rec, fromDate, toDate){
  // Use dt_prev when present; otherwise dt_real
  const base = safeDate(rec.dt_prev) ? rec.dt_prev : rec.dt_real;
  const d = safeDate(base);
  if(!d) return false;
  const t = d.getTime();
  if(fromDate){
    const f = safeDate(fromDate).getTime();
    if(t < f) return false;
  }
  if(toDate){
    const tt = safeDate(toDate).getTime();
    if(t > tt) return false;
  }
  return true;
}

function filteredData(){
  const f = getFilterState();
  return data.filter(rec=>{
    if(f.carFilter !== "__ALL__" && rec.carro !== f.carFilter) return false;
    if(f.modelFilter !== "__ALL__" && rec.modelo !== f.modelFilter) return false;
    if(f.respFilter !== "__ALL__" && rec.responsavel !== f.respFilter) return false;
    if(f.phaseFilter !== "__ALL__" && rec.fase !== f.phaseFilter) return false;
    if(f.statusFilter !== "__ALL__" && rec.status !== f.statusFilter) return false;
    if(f.onlyPending && rec.status !== STATUS.NAO) return false;
    if(f.taskSearch && !rec.tarefa.toLowerCase().includes(f.taskSearch)) return false;

    if(f.fromDate || f.toDate){
      return inDateRange(rec, f.fromDate, f.toDate);
    }
    return true;
  });
}

/** =========================
 *  FILTER OPTIONS
 * ========================= */
function rebuildFilters(){
  const cars = Array.from(new Set(data.map(d=>d.carro))).sort();
  const models = Array.from(new Set(data.map(d=>d.modelo))).sort();
  const resps = Array.from(new Set(data.map(d=>d.responsavel))).sort();
  const phases = Array.from(new Set(data.map(d=>d.fase))).sort();

  function fillSel(selId, values){
    const sel = $(selId);
    const current = sel.value;
    sel.innerHTML = `<option value="__ALL__">Todos</option>` + values.map(v=>`<option value="${escapeHtml(v)}">${escapeHtml(v)}</option>`).join("");
    // try keep
    if(values.includes(current)) sel.value = current;
  }
  fillSel("carFilter", cars);
  fillSel("modelFilter", models);
  fillSel("respFilter", resps);
  fillSel("phaseFilter", phases);
}

function escapeHtml(s){
  return String(s).replaceAll("&","&amp;").replaceAll("<","&lt;").replaceAll(">","&gt;").replaceAll('"',"&quot;").replaceAll("'","&#039;");
}

/** =========================
 *  CHARTS
 * ========================= */
let charts = {};

function toast(msg){
  const t = $("toast");
  t.textContent = msg;
  t.classList.add("show");
  clearTimeout(toast._timer);
  toast._timer = setTimeout(()=>t.classList.remove("show"), 3200);
}

function destroyCharts(){
  for(const k in charts){
    try{ charts[k].destroy(); }catch(e){}
  }
  charts = {};
}

function renderAll(){
  const fdata = filteredData();
  $("filterCount").textContent = `Registros no escopo: ${fdata.length}`;
  $("scopeText").textContent = `${fdata.length} tarefas • ${$("naMode").value==="exclude" ? "N.A. excluído" : "N.A. incluso"}`;

  // KPI calculations
  const considered = fdata.filter(r=>{
    if(getFilterState().naMode === "exclude") return r.status !== STATUS.NA;
    return true;
  });

  const total = considered.length;
  const sim = considered.filter(r=>r.status===STATUS.SIM).length;
  const nao = considered.filter(r=>r.status===STATUS.NAO).length;

  const pct = (n)=> total ? (100*n/total) : 0;
  const kpiSim = total ? pct(sim) : 0;
  const kpiNao = total ? pct(nao) : 0;

  const naAll = fdata.filter(r=>r.status===STATUS.NA).length;
  const kpiNA = fdata.length ? (100*naAll/fdata.length) : 0;

  // atraso computations for records with both dates
  const delays = fdata.map(r => daysDiff(r.dt_real, r.dt_prev)).filter(v=>typeof v==="number" && Number.isFinite(v));
  const atrasoMed = median(delays);
  const within = delays.filter(d=>d<=0).length;
  const atrasoMaior = delays.filter(d=>d>=8).length;

  const kpiDentro = delays.length ? (100*within/delays.length) : 0;
  const kpiAtrasoMaior = delays.length ? (100*atrasoMaior/delays.length) : 0;

  $("kpiTotal").textContent = total.toLocaleString("pt-BR");
  $("kpiSim").textContent = kpiSim.toFixed(1).replace(".",",") + "%";
  $("kpiNao").textContent = kpiNao.toFixed(1).replace(".",",") + "%";
  $("kpiNA").textContent = kpiNA.toFixed(1).replace(".",",") + "%";
  $("kpiPendencias").textContent = fdata.filter(r=>r.status===STATUS.NAO).length.toLocaleString("pt-BR");
  $("kpiAtrasoMed").textContent = (atrasoMed===null ? "—" : atrasoMed.toFixed(1).replace(".",",")) ;
  $("kpiDentro").textContent = kpiDentro.toFixed(1).replace(".",",") + "%";
  $("kpiAtrasoMaior").textContent = kpiAtrasoMaior.toFixed(1).replace(".",",") + "%";

  // Table details
  const pendingOrStatus = (() => {
    const st = $("statusFilter").value;
    const onlyPending = $("onlyPending").value === "yes";
    if(onlyPending) return fdata.filter(r=>r.status===STATUS.NAO);
    if(st !== "__ALL__") return fdata.filter(r=>r.status===st);
    return fdata.slice();
  })();

  // sort: pending first then by phase then delay desc
  pendingOrStatus.sort((a,b)=>{
    const pa = a.status===STATUS.NAO ? 0 : 1;
    const pb = b.status===STATUS.NAO ? 0 : 1;
    if(pa!==pb) return pa-pb;
    if(a.fase!==b.fase) return a.fase.localeCompare(b.fase);
    const da = daysDiff(a.dt_real,a.dt_prev);
    const db = daysDiff(b.dt_real,b.dt_prev);
    if((da===null)!=(db===null)) return da===null ? 1 : -1;
    if(da===null) return 0;
    return (db-da); // desc
  });

  const tbody = document.querySelector("#tableDetails tbody");
  tbody.innerHTML = "";
  const top = pendingOrStatus.slice(0,60);
  top.forEach((r,idx)=>{
    const delay = daysDiff(r.dt_real, r.dt_prev);
    const tr = document.createElement("tr");
    tr.innerHTML = `
      <td>${idx+1}</td>
      <td>${escapeHtml(r.carro)}<br/><span class="muted">${escapeHtml(r.modelo||"")}</span></td>
      <td>${escapeHtml(r.fase)}</td>
      <td>${escapeHtml(r.tarefa)}</td>
      <td>${escapeHtml(r.responsavel)}</td>
      <td><span class="${statusPillClass(r.status)}">${r.status}</span></td>
      <td>${fmtDate(r.dt_prev)}</td>
      <td>${fmtDate(r.dt_real)}</td>
      <td>${delay===null ? "—" : delay.toString()}</td>
    `;
    tr.style.cursor="pointer";
    tr.onclick = ()=>{
      // drilldown: set phase filter if clicked row has phase
      $("phaseFilter").value = r.fase;
      $("taskSearch").value = "";
      $("statusFilter").value = "__ALL__";
      $("onlyPending").value = "no";
      applyAndRender();
    };
    tbody.appendChild(tr);
  });

  // Create charts data
  const byPhase = {};
  for(const r of fdata){
    byPhase[r.fase] ??= {SIM:0, NAO:0, NA:0, total:0};
    byPhase[r.fase][r.status] = (byPhase[r.fase][r.status]||0)+1;
    byPhase[r.fase].total++;
  }
  const phaseLabels = Object.keys(byPhase).sort((a,b)=>a.localeCompare(b));
  const simArr = phaseLabels.map(p=>byPhase[p].SIM);
  const naoArr = phaseLabels.map(p=>byPhase[p].NAO);
  const naArr  = phaseLabels.map(p=>byPhase[p].NA);

  // Chart 1: stacked by phase
  charts.chartPhaseStack = new Chart($("chartPhaseStack"),{
    type:"bar",
    data:{
      labels: phaseLabels,
      datasets:[
        {label:"SIM", data: simArr, backgroundColor:"rgba(46,204,113,.85)"},
        {label:"NÃO", data: naoArr, backgroundColor:"rgba(231,76,60,.85)"},
        {label:"N.A.", data: naArr, backgroundColor:"rgba(241,196,15,.85)"}
      ]
    },
    options:{
      responsive:true,
      plugins:{
        legend:{labels:{color:"#e7efff"}},
        tooltip:{callbacks:{
          label:(ctx)=>{
            const val = ctx.raw ?? 0;
            const phase = ctx.label;
            const total = byPhase[phase].total || 0;
            const pctVal = total ? (100*val/total) : 0;
            return `${ctx.dataset.label}: ${val} (${pctVal.toFixed(1).replace(".",",")}%)`;
          }
        }}
      },
      scales:{
        x:{ticks:{color:"#cfe0ff"}},
        y:{ticks:{color:"#cfe0ff"}, grid:{color:"rgba(255,255,255,.06)"}},
      },
      onClick:(evt,els)=>{
        if(!els || !els.length) return;
        const idx = els[0].index;
        const phase = phaseLabels[idx];
        $("phaseFilter").value = phase;
        $("statusFilter").value="__ALL__";
        $("onlyPending").value="no";
        applyAndRender();
      }
    }
  });

  // Chart 2: Top10 by NÃO rate (exclude NA from denom by default)
  const byTask = {};
  for(const r of fdata){
    if(!byTask[r.tarefa]) byTask[r.tarefa]={SIM:0,NAO:0,NA:0,total:0,totalNoNA:0};
    byTask[r.tarefa][r.status]=(byTask[r.tarefa][r.status]||0)+1;
    byTask[r.tarefa].total++;
    if(r.status!==STATUS.NA) byTask[r.tarefa].totalNoNA++;
  }
  const taskList = Object.keys(byTask).map(t=>{
    const o = byTask[t];
    const denom = (getFilterState().naMode==="exclude") ? o.totalNoNA : o.total;
    const pctNao = denom ? (100*o.NAO/denom) : 0;
    return {t, ...o, pctNao};
  }).sort((a,b)=>b.pctNao-a.pctNao).slice(0,10);

  charts.chartTopNao = new Chart($("chartTopNao"),{
    type:"bar",
    data:{
      labels: taskList.map(x=>x.t.length>30?x.t.slice(0,30)+"…":x.t),
      datasets:[{
        label:"Taxa de NÃO (%)",
        data: taskList.map(x=>x.pctNao),
        backgroundColor: taskList.map(x=> x.pctNao>=20 ? "rgba(231,76,60,.85)" : "rgba(74,163,255,.7)")
      }]
    },
    options:{
      responsive:true,
      plugins:{legend:{labels:{color:"#e7efff"}}, tooltip:{callbacks:{
        label:(ctx)=>{
          const item = taskList[ctx.dataIndex];
          return `NÃO: ${item.NAO} | SIM: ${item.SIM} | N.A.: ${item.NA} | taxa: ${item.pctNao.toFixed(1).replace(".",",")}%`;
        }
      }}},
      scales:{
        x:{ticks:{color:"#cfe0ff"}},
        y:{ticks:{color:"#cfe0ff"}, grid:{color:"rgba(255,255,255,.06)"}}
      },
      onClick:(evt,els)=>{
        if(!els || !els.length) return;
        const item = taskList[els[0].index];
        $("taskSearch").value = "";
        $("phaseFilter").value="__ALL__";
        $("statusFilter").value="__ALL__";
        $("onlyPending").value="yes";
        // Keep search to this task to drill
        $("taskSearch").value = item.t.split(" ").slice(0,3).join(" ");
        applyAndRender();
      }
    }
  });

  // Chart 3: Pareto (80/20) of pendências (NÃO counts by task)
  const totalNao = Object.values(byTask).reduce((acc,o)=>acc+o.NAO,0);
  const pareto = Object.keys(byTask).map(t=>({t, nao:byTask[t].NAO})).sort((a,b)=>b.nao-a.nao);
  let cum=0;
  const paretoTop = pareto.slice(0, Math.min(12, pareto.length));
  const labels = paretoTop.map(x=>x.t.length>26?x.t.slice(0,26)+"…":x.t);
  const naoVals = paretoTop.map(x=>x.nao);
  const cumPct = paretoTop.map(x=>{
    cum += x.nao;
    return totalNao ? (100*cum/totalNao) : 0;
  });

  charts.chartPareto = new Chart($("chartPareto"),{
    type:"bar",
    data:{
      labels,
      datasets:[
        {label:"Qtd. NÃO", data: naoVals, backgroundColor:"rgba(231,76,60,.75)"},
        {label:"% Acumulado", type:"line", data: cumPct, borderColor:"rgba(74,163,255,.95)", backgroundColor:"rgba(74,163,255,.2)", yAxisID:"y1", tension:.25}
      ]
    },
    options:{
      responsive:true,
      plugins:{
        legend:{labels:{color:"#e7efff"}},
        tooltip:{callbacks:{
          label:(ctx)=>{
            const idx = ctx.dataIndex;
            if(ctx.dataset.type==="line"){
              return `Acumulado: ${cumPct[idx].toFixed(1).replace(".",",")}%`;
            }
            return `NÃO: ${naoVals[idx]}`;
          }
        }}
      },
      scales:{
        x:{ticks:{color:"#cfe0ff"}},
        y:{ticks:{color:"#cfe0ff"}, grid:{color:"rgba(255,255,255,.06)"}},
        y1:{position:"right", ticks:{color:"#cfe0ff"}, grid:{drawOnChartArea:false}, min:0, max:100}
      }
    }
  });

  // Heatmap: Task x Responsável (taxa SIM)
  const respSet = Array.from(new Set(fdata.map(r=>r.responsavel))).sort();
  const taskSet = Object.keys(byTask).sort((a,b)=>byTask[b].NAO - byTask[a].NAO).slice(0,12);
  const topResp = respSet.slice(0,8);

  // build matrix
  const matrix = taskSet.map(t=> topResp.map(resp=>{
    const sub = fdata.filter(r=>r.tarefa===t && r.responsavel===resp);
    const denom = (getFilterState().naMode==="exclude") ? sub.filter(x=>x.status!==STATUS.NA).length : sub.length;
    const simC = sub.filter(x=>x.status===STATUS.SIM).length;
    return denom ? simC/denom : null;
  }));

  // Heatmap using Chart.js "matrix" style by drawing colored rect via scatter
  // We'll emulate with bubble/scatter:
  const heatPoints = [];
  const cols = topResp.length;
  const rows = taskSet.length;

  for(let i=0;i<rows;i++){
    for(let j=0;j<cols;j++){
      const v = matrix[i][j];
      if(v===null) continue;
      // v 0..1
      const alpha = 0.15 + 0.85*v;
      const color = `rgba(46,204,113,${alpha})`;
      heatPoints.push({x:j, y:i, v, color});
    }
  }

  charts.heatmap = new Chart($("heatmap"),{
    type:"scatter",
    data:{
      datasets:[{
        label:"Taxa SIM (0..1)",
        data: heatPoints,
        backgroundColor: heatPoints.map(p=>p.color),
        pointRadius: 12,
      }]
    },
    options:{
      plugins:{
        legend:{labels:{color:"#e7efff"}},
        tooltip:{
          callbacks:{
            label:(ctx)=>{
              const p = ctx.raw;
              const i = p.y, j = p.x;
              const t = taskSet[i];
              const resp = topResp[j];
              const pct = (p.v*100).toFixed(1).replace(".",",");
              return `${resp} • ${t.slice(0,45)}${t.length>45?"…":""}\nTaxa SIM: ${pct}%`;
            }
          }
        }
      },
      scales:{
        x:{type:"linear", position:"bottom", min:-0.5, max:cols-0.5, ticks:{
          color:"#cfe0ff",
          callback:(val)=> topResp[Math.round(val)] ? (topResp[Math.round(val)].length>10?topResp[Math.round(val)].slice(0,10)+"…":topResp[Math.round(val)]) : ""
        }, grid:{color:"rgba(255,255,255,.06)"}},
        y:{type:"linear", min:-0.5, max:rows-0.5, ticks:{
          color:"#cfe0ff",
          stepSize:1,
          callback:(val)=> taskSet[Math.round(val)] ? (taskSet[Math.round(val)].length>22?taskSet[Math.round(val)].slice(0,22)+"…":taskSet[Math.round(val)]) : ""
        }, grid:{color:"rgba(255,255,255,.06)'}}
      }
    }
  });

  // Histograma atrasos
  // bucket: -5..15 step 2
  const delaysArr = delays.slice();
  const buckets = [];
  for(let b=-6;b<=16;b+=2) buckets.push(b);
  const bucketCounts = buckets.map(()=>0);
  for(const d of delaysArr){
    // find interval
    for(let i=0;i<buckets.length-1;i++){
      if(d>=buckets[i] && d<buckets[i+1]){ bucketCounts[i]++; break; }
    }
    if(d>=buckets[buckets.length-1]) bucketCounts[buckets.length-1]++; // last
  }
  const bucketLabels = buckets.map((b,i)=>{
    const next = buckets[i+1];
    return next!==undefined ? `${b}..${next-1}` : `${b}+`;
  });

  charts.histAtraso = new Chart($("histAtraso"),{
    type:"bar",
    data:{labels:bucketLabels, datasets:[{label:"Qtd. ocorrências", data:bucketCounts, backgroundColor:"rgba(74,163,255,.75)"}]},
    options:{
      plugins:{legend:{labels:{color:"#e7efff"}}},
      scales:{
        x:{ticks:{color:"#cfe0ff"}, grid:{color:"rgba(255,255,255,.06)"}},
        y:{ticks:{color:"#cfe0ff"}, grid:{color:"rgba(255,255,255,.06)"}}
      }
    }
  });

  // Scatter: for each task compute %NAO vs atraso mediano
  const scatterTasks = taskList.map(t=>{
    const denom = (getFilterState().naMode==="exclude") ? byTask[t.t].totalNoNA : byTask[t.t].total;
    const pctNao = denom ? (100*byTask[t.t].NAO/denom) : 0;
    const subDelays = fdata.filter(r=>r.tarefa===t.t).map(r=>daysDiff(r.dt_real,r.dt_prev)).filter(v=>typeof v==="number");
    const med = median(subDelays);
    return {t:t.t, x:pctNao, y: med===null?0:med, med, has: med!==null};
  }).filter(p=>p.has).slice(0,24);

  charts.scatterNaoVsAtraso = new Chart($("scatterNaoVsAtraso"),{
    type:"scatter",
    data:{
      datasets:[{
        label:"Tarefas",
        data: scatterTasks.map(p=>({x:p.x, y:p.y})),
        pointRadius:5,
        backgroundColor:"rgba(155,89,182,.85)",
      }]
    },
    options:{
      plugins:{
        legend:{labels:{color:"#e7efff"}},
        tooltip:{callbacks:{
          label:(ctx)=>{
            const pt = ctx.raw;
            const closest = scatterTasks.reduce((best,cur)=>{
              if(Math.abs(cur.x-pt.x)+Math.abs(cur.y-pt.y) < best.d) return {cur, d:Math.abs(cur.x-pt.x)+Math.abs(cur.y-pt.y)};
              return best;
            },{cur:null,d:1e9}).cur;
            return `${closest.t.length>35?closest.t.slice(0,35)+"…":closest.t}\n%NÃO: ${closest.x.toFixed(1).replace(".",",")}%\nAtraso mediano: ${closest.med.toFixed(1).replace(".",",")} dias`;
          }
        }}
      },
      scales:{
        x:{ticks:{color:"#cfe0ff"}, grid:{color:"rgba(255,255,255,.06)"}, title:{display:true, text:"% NÃO", color:"#cfe0ff"}},
        y:{ticks:{color:"#cfe0ff"}, grid:{color:"rgba(255,255,255,.06)"}, title:{display:true, text:"Atraso mediano (dias)", color:"#cfe0ff"}}
      },
      onClick:(evt,els)=>{
        if(!els || !els.length) return;
        const pt = charts.scatterNaoVsAtraso.getElementsAtEventForMode(evt,'nearest',{intersect:true},false)[0];
        if(!pt) return;
        const i = pt.index;
        const item = scatterTasks[i];
        if(!item) return;
        $("onlyPending").value="no";
        $("taskSearch").value = item.t.split(" ").slice(0,3).join(" ");
        applyAndRender();
      }
    }
  });

  // Timeline: group by week of dt_prev, compute avg %SIM per week (exclude NA optionally)
  const weekBuckets = new Map();
  function weekKey(dateStr){
    const d = safeDate(dateStr); if(!d) return null;
    // ISO-like week start (Monday)
    const day = (d.getUTCDay()+6)%7; // Mon=0
    const monday = new Date(d.getTime() - day*24*3600*1000);
    return monday.toISOString().slice(0,10);
  }

  for(const r of fdata){
    const key = weekKey(r.dt_prev);
    if(!key) continue;
    if(!weekBuckets.has(key)) weekBuckets.set(key, {sim:0, denom:0, nao:0, na:0});
    const o = weekBuckets.get(key);
    if(getFilterState().naMode==="exclude" && r.status===STATUS.NA) {
      o.na++; // track only
      continue;
    }
    if(r.status===STATUS.SIM) o.sim++;
    if(r.status===STATUS.NAO) o.nao++;
    if(r.status===STATUS.NA) o.na++;
    o.denom++;
  }

  const wk = Array.from(weekBuckets.entries()).sort((a,b)=>a[0].localeCompare(b[0]));
  const labelsW = wk.map(x=>x[0]);
  const pctSimW = wk.map(([k,o])=>{
    const denom = o.denom || 0;
    return denom ? (100*o.sim/denom) : 0;
  });

  charts.timeline = new Chart($("timeline"),{
    type:"line",
    data:{
      labels: labelsW,
      datasets:[{
        label:"% SIM por semana",
        data: pctSimW,
        borderColor:"rgba(74,163,255,.95)",
        backgroundColor:"rgba(74,163,255,.15)",
        fill:true,
        tension:.25,
        pointRadius:4
      }]
    },
    options:{
      plugins:{
        legend:{labels:{color:"#e7efff"}},
        tooltip:{callbacks:{
          label:(ctx)=>{
            return `%SIM: ${ctx.raw.toFixed(1).replace(".",",")}%`;
          }
        }}
      },
      scales:{
        x:{ticks:{color:"#cfe0ff"}, grid:{color:"rgba(255,255,255,.06)'}},
        y:{ticks:{color:"#cfe0ff"}, grid:{color:"rgba(255,255,255,.06)'} , suggestedMin:0, suggestedMax:100}
      }
    }
  });
}

/** apply filters with chart refresh */
function applyAndRender(){
  destroyCharts();
  renderAll();
}

/** =========================
 *  UI EVENTS
 * ========================= */
function resetFilters(){
  $("fromDate").value = "";
  $("toDate").value = "";
  $("carFilter").value = "__ALL__";
  $("modelFilter").value = "__ALL__";
  $("respFilter").value = "__ALL__";
  $("phaseFilter").value = "__ALL__";
  $("statusFilter").value = "__ALL__";
  $("taskSearch").value = "";
  $("onlyPending").value = "no";
  $("naMode").value = "exclude";
}

function exportFilters(){
  const st = getFilterState();
  const payload = {
    generatedAt: new Date().toISOString(),
    filter: st
  };
  const blob = new Blob([JSON.stringify(payload,null,2)], {type:"application/json"});
  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  a.href = url; a.download = "dashboard-filtros.json";
  a.click();
  URL.revokeObjectURL(url);
}

$("btnApply").addEventListener("click", applyAndRender);
$("btnReset").addEventListener("click", ()=>{
  resetFilters();
  applyAndRender();
});
$("btnLoadSample").addEventListener("click", ()=>{
  seedData();
  rebuildFilters();
  resetFilters();
  toast("Dados de exemplo restaurados.");
  applyAndRender();
});
$("btnExport").addEventListener("click", exportFilters);
$("csvFile").addEventListener("change", async (e)=>{
  const file = e.target.files && e.target.files[0];
  if(!file) return;
  await loadCSVFile(file);
  // keep filters; just re-render
  applyAndRender();
});

function init(){
  seedData();
  rebuildFilters();
  resetFilters();
  // default date range: from 2026-01-01 to 2026-12-31
  $("fromDate").value = "2026-01-01";
  $("toDate").value = "2026-12-31";
  applyAndRender();
}
init();
</script>
</body>
</html>
