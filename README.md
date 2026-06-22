
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Dashboard Fase Elétrica - Globe (Entrada Manual)</title>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-adapter-date-fns/dist/chartjs-adapter-date-fns.bundle.min.js"></script>
<style>
:root{--bg:#0b1220;--panel:#121a2e;--panel2:#172142;--border:#243056;--text:#e6ecff;--muted:#8da0c7;
--accent:#3b82f6;--ok:#22c55e;--warn:#f59e0b;--bad:#ef4444;--info:#06b6d4;--purple:#a855f7;}
*{box-sizing:border-box}
body{margin:0;font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;background:var(--bg);color:var(--text);font-size:14px}
header{padding:18px 28px;background:linear-gradient(135deg,#0f1a35,#1e1148);border-bottom:1px solid var(--border);
display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px}
header h1{margin:0;font-size:20px}
header .sub{color:var(--muted);font-size:12px;margin-top:4px}
.btn{background:var(--accent);color:#fff;border:0;padding:9px 14px;border-radius:8px;font-weight:600;cursor:pointer;font-size:13px}
.btn:hover{background:#2563eb}
.btn.ghost{background:var(--panel2);border:1px solid var(--border)}
.btn.danger{background:var(--bad)}
.btn.ok{background:var(--ok)}
.tabs{display:flex;gap:6px;padding:0 28px;background:var(--panel);border-bottom:1px solid var(--border)}
.tab{padding:14px 18px;cursor:pointer;color:var(--muted);font-weight:600;border-bottom:3px solid transparent;font-size:13px}
.tab.active{color:var(--text);border-color:var(--accent)}
.container{padding:20px 28px;max-width:1600px;margin:0 auto}
.view{display:none}.view.active{display:block}

.filters,.formgrid{background:var(--panel);border:1px solid var(--border);border-radius:12px;padding:16px;margin-bottom:20px;
display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:12px}
label{display:flex;flex-direction:column;gap:6px;font-size:11px;color:var(--muted);text-transform:uppercase;letter-spacing:.5px}
select,input,textarea{background:var(--panel2);border:1px solid var(--border);color:var(--text);padding:8px 10px;
border-radius:8px;font-size:13px;outline:none;font-family:inherit}
select:focus,input:focus,textarea:focus{border-color:var(--accent)}
.formgrid .full{grid-column:1/-1}
.formgrid .actions{display:flex;gap:10px;align-items:end}

.kpis{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:14px;margin-bottom:20px}
.kpi{background:var(--panel);border:1px solid var(--border);border-radius:12px;padding:16px;position:relative;overflow:hidden}
.kpi::before{content:"";position:absolute;left:0;top:0;bottom:0;width:4px;background:var(--accent)}
.kpi.ok::before{background:var(--ok)}.kpi.warn::before{background:var(--warn)}
.kpi.bad::before{background:var(--bad)}.kpi.info::before{background:var(--info)}.kpi.purple::before{background:var(--purple)}
.kpi .label{font-size:11px;color:var(--muted);text-transform:uppercase;margin-bottom:8px}
.kpi .value{font-size:26px;font-weight:700}
.kpi .hint{font-size:11px;color:var(--muted);margin-top:4px}

.grid{display:grid;grid-template-columns:repeat(12,1fr);gap:16px}
.card{background:var(--panel);border:1px solid var(--border);border-radius:12px;padding:16px}
.card h3{margin:0 0 12px 0;font-size:14px;font-weight:600}
.c-12{grid-column:span 12}.c-8{grid-column:span 8}.c-6{grid-column:span 6}.c-4{grid-column:span 4}
@media(max-width:1100px){.c-8,.c-6,.c-4{grid-column:span 12}}
.chart-wrap{position:relative;height:280px}
.chart-wrap.tall{height:360px}

table{width:100%;border-collapse:collapse;font-size:12px}
th,td{padding:8px 10px;text-align:left;border-bottom:1px solid var(--border)}
th{color:var(--muted);text-transform:uppercase;font-size:10px;background:var(--panel)}
.scroll{max-height:480px;overflow:auto}
.badge{padding:2px 8px;border-radius:10px;font-size:11px;font-weight:600}
.b-ok{background:rgba(34,197,94,.15);color:#4ade80}
.b-warn{background:rgba(245,158,11,.15);color:#fbbf24}
.b-bad{background:rgba(239,68,68,.15);color:#f87171}
.b-info{background:rgba(6,182,212,.15);color:#22d3ee}
.b-muted{background:rgba(100,116,139,.2);color:#94a3b8}

.empty{text-align:center;padding:40px;color:var(--muted)}
.toolbar{display:flex;gap:10px;margin-bottom:14px;flex-wrap:wrap}
.row-actions button{background:transparent;border:0;color:var(--muted);cursor:pointer;font-size:14px;padding:2px 6px}
.row-actions button:hover{color:var(--text)}
.legend{display:flex;gap:14px;font-size:11px;color:var(--muted);margin-top:8px;flex-wrap:wrap}
.legend i{display:inline-block;width:10px;height:10px;border-radius:2px;margin-right:5px}
.gantt-row{display:grid;grid-template-columns:160px 1fr;gap:8px;align-items:center;margin-bottom:6px;font-size:11px}
.gantt-bar-track{position:relative;height:22px;background:var(--panel2);border-radius:4px}
.gantt-bar{position:absolute;height:100%;border-radius:4px}
.toast{position:fixed;bottom:24px;right:24px;background:var(--ok);color:#fff;padding:12px 18px;border-radius:8px;
font-weight:600;opacity:0;transform:translateY(10px);transition:.25s;z-index:1000}
.toast.show{opacity:1;transform:translateY(0)}
.toast.err{background:var(--bad)}
footer{text-align:center;padding:24px;color:var(--muted);font-size:11px}
</style>
</head>
<body>
<header>
  <div>
    <h1>⚡ Dashboard Fase Elétrica - Globe</h1>
    <div class="sub">Entrada manual de dados · Persistência local · Baseado no checklist Globe_Fase_Eletrica</div>
  </div>
  <div style="display:flex;gap:8px;flex-wrap:wrap">
    <button class="btn ghost" onclick="exportJSON()">⬇ Exportar JSON</button>
    <button class="btn ghost" onclick="document.getElementById('imp').click()">⬆ Importar</button>
    <input type="file" id="imp" accept=".json" style="display:none" onchange="importJSON(event)">
    <button class="btn ghost" onclick="loadSample()">🎲 Dados de exemplo</button>
    <button class="btn danger" onclick="clearAll()">🗑 Limpar tudo</button>
  </div>
</header>

<div class="tabs">
  <div class="tab active" data-view="entrada">📝 Entrada de Dados</div>
  <div class="tab" data-view="dashboard">📊 Dashboard</div>
  <div class="tab" data-view="ajuda">❓ Como usar</div>
</div>

<div class="container">

<!-- VIEW: ENTRADA -->
<div id="view-entrada" class="view active">
  <div class="formgrid">
    <label>Veículo (chassi/código)
      <input id="i-veiculo" placeholder="ex: GLB-2026-001" list="lst-veiculos">
      <datalist id="lst-veiculos"></datalist>
    </label>
    <label>Fase
      <select id="i-fase"></select>
    </label>
    <label>Tarefa
      <select id="i-tarefa"></select>
    </label>
    <label>Responsável
      <input id="i-responsavel" placeholder="Nome" list="lst-resp">
      <datalist id="lst-resp"></datalist>
    </label>
    <label>Previsto - início
      <input type="date" id="i-prev-ini">
    </label>
    <label>Previsto - fim
      <input type="date" id="i-prev-fim">
    </label>
    <label>Real - início
      <input type="date" id="i-real-ini">
    </label>
    <label>Real - fim
      <input type="date" id="i-real-fim">
    </label>
    <label>Status
      <select id="i-status">
        <option>Não iniciado</option><option>Em andamento</option>
        <option>Concluído</option><option>Atrasado</option>
      </select>
    </label>
    <label>Rubrica/conferência
      <select id="i-rubrica"><option value="nao">Não</option><option value="sim">Sim</option></select>
    </label>
    <label class="full">Observação (opcional)
      <input id="i-obs" maxlength="200" placeholder="Notas, retrabalhos, etc.">
    </label>
    <div class="actions full">
      <button class="btn ok" onclick="saveTask()">💾 Salvar tarefa</button>
      <button class="btn ghost" onclick="resetForm()">Limpar campos</button>
      <span id="edit-info" style="color:var(--muted);font-size:12px;align-self:center"></span>
    </div>
  </div>

  <div class="card">
    <div class="toolbar">
      <input id="search" placeholder="🔍 Buscar..." oninput="renderTable()" style="flex:1;min-width:200px">
      <select id="ft-veic" onchange="renderTable()"><option value="">Todos veículos</option></select>
      <select id="ft-fase" onchange="renderTable()"><option value="">Todas fases</option></select>
      <select id="ft-status" onchange="renderTable()"><option value="">Todos status</option></select>
    </div>
    <div class="scroll"><table>
      <thead><tr><th>Veículo</th><th>Fase</th><th>Tarefa</th><th>Responsável</th>
      <th>Prev. ini</th><th>Prev. fim</th><th>Real ini</th><th>Real fim</th>
      <th>Status</th><th>Rubrica</th><th>Atraso</th><th></th></tr></thead>
      <tbody id="tbl-body"></tbody>
    </table></div>
  </div>
</div>

<!-- VIEW: DASHBOARD -->
<div id="view-dashboard" class="view">
  <div class="filters">
    <label>Veículo<select id="f-veiculo"><option value="">Todos</option></select></label>
    <label>Fase<select id="f-fase"><option value="">Todas</option></select></label>
    <label>Categoria<select id="f-categoria"><option value="">Todas</option></select></label>
    <label>Responsável<select id="f-responsavel"><option value="">Todos</option></select></label>
    <label>Status<select id="f-status"><option value="">Todos</option></select></label>
    <label>Faixa de atraso
      <select id="f-atraso"><option value="">Todas</option>
      <option value="no">No prazo</option><option value="1-3">1-3 d</option>
      <option value="4-7">4-7 d</option><option value="8+">8+ d</option></select>
    </label>
    <label>Rubrica
      <select id="f-rubrica"><option value="">Todas</option>
      <option value="sim">Com</option><option value="nao">Sem</option></select>
    </label>
    <label>Data (de)<input type="date" id="f-data-de"></label>
    <label>Data (até)<input type="date" id="f-data-ate"></label>
    <button class="btn" onclick="resetFilters()">Limpar filtros</button>
  </div>

  <div id="empty-dash" class="empty card" style="display:none">
    Nenhum dado ainda. Vá em <b>📝 Entrada de Dados</b> ou clique em <b>🎲 Dados de exemplo</b>.
  </div>

  <div id="dash-content">
    <div class="kpis" id="kpis"></div>

    <div class="grid">
      <div class="card c-8"><h3>📈 Conclusão acumulada</h3><div class="chart-wrap"><canvas id="ch-burndown"></canvas></div></div>
      <div class="card c-4"><h3>🎯 % por Fase</h3><div class="chart-wrap"><canvas id="ch-fase"></canvas></div></div>

      <div class="card c-6"><h3>📊 Previsto vs Realizado</h3><div class="chart-wrap"><canvas id="ch-prevreal"></canvas></div></div>
      <div class="card c-6"><h3>🚦 Status Geral</h3><div class="chart-wrap"><canvas id="ch-status"></canvas></div></div>

      <div class="card c-8"><h3>🔥 Status por Categoria (empilhado)</h3><div class="chart-wrap"><canvas id="ch-stack"></canvas></div></div>
      <div class="card c-4"><h3>🍩 Distribuição por Categoria</h3><div class="chart-wrap"><canvas id="ch-cat"></canvas></div></div>

      <div class="card c-6"><h3>👷 Ranking Responsáveis</h3><div class="chart-wrap tall"><canvas id="ch-resp"></canvas></div></div>
      <div class="card c-6"><h3>⏱️ Atraso médio por Responsável</h3><div class="chart-wrap tall"><canvas id="ch-resp-atraso"></canvas></div></div>

      <div class="card c-8"><h3>🎯 Pareto - tarefas que mais atrasam</h3><div class="chart-wrap"><canvas id="ch-pareto"></canvas></div></div>
      <div class="card c-4"><h3>🪣 Faixas de atraso</h3><div class="chart-wrap"><canvas id="ch-faixas"></canvas></div></div>

      <div class="card c-12"><h3>📅 Gantt - Veículos x Fases</h3>
        <div id="gantt" style="max-height:420px;overflow:auto"></div>
        <div class="legend">
          <span><i style="background:#3b82f6"></i>Fase 1</span>
          <span><i style="background:#a855f7"></i>Fase 2</span>
          <span><i style="background:#06b6d4"></i>Fase 3</span>
          <span><i style="background:#ef4444"></i>Atraso</span>
        </div>
      </div>

      <div class="card c-6"><h3>📆 Atrasos por dia da semana</h3><div class="chart-wrap"><canvas id="ch-dow"></canvas></div></div>
      <div class="card c-6"><h3>📦 Carga atual (tarefas abertas)</h3><div class="chart-wrap"><canvas id="ch-carga"></canvas></div></div>

      <div class="card c-12"><h3>⚠️ Tarefas em atraso</h3>
        <div class="scroll"><table id="tbl-atraso">
          <thead><tr><th>Veículo</th><th>Fase</th><th>Tarefa</th><th>Responsável</th>
          <th>Prev. fim</th><th>Real fim</th><th>Atraso (d)</th><th>Status</th></tr></thead>
          <tbody></tbody></table></div>
      </div>
    </div>
  </div>
</div>

<!-- VIEW: AJUDA -->
<div id="view-ajuda" class="view">
  <div class="card">
    <h3>Como usar este dashboard</h3>
    <ol style="line-height:1.8">
      <li><b>Entrada de dados:</b> preencha o formulário com os dados de cada tarefa do checklist da fase elétrica. As tarefas oferecidas no menu vêm do PDF Globe_Fase_Eletrica.</li>
      <li><b>Persistência:</b> tudo é salvo automaticamente no seu navegador (localStorage). Não precisa de internet nem servidor.</li>
      <li><b>Editar/excluir:</b> use os ícones ✏️ e 🗑 na tabela de tarefas.</li>
      <li><b>Backup:</b> use <b>Exportar JSON</b> para baixar e <b>Importar</b> para restaurar — ideal para compartilhar entre máquinas.</li>
      <li><b>Dashboard:</b> mude para a aba <b>📊 Dashboard</b> para ver KPIs, gráficos e o Gantt. Filtros no topo afetam todos os gráficos.</li>
      <li><b>Dados de exemplo:</b> botão <b>🎲</b> popula 60+ tarefas para você visualizar como fica preenchido.</li>
    </ol>
    <h3 style="margin-top:24px">Indicadores incluídos</h3>
    <p style="color:var(--muted);line-height:1.7">% conclusão geral e por fase · Aderência ao prazo · Atraso médio · Tarefas em atraso · Veículos concluídos · Lead time médio · Tarefas sem rubrica · Burn-up · Previsto vs Realizado · Pareto de atrasos · Ranking de responsáveis · Carga de trabalho · Gantt por veículo · Atrasos por dia da semana · Faixas de atraso.</p>
  </div>
</div>

</div>
<div id="toast" class="toast"></div>
<footer>Dados salvos localmente neste navegador · Faça exportações periódicas como backup</footer>

<script>
// ---- Catálogo do checklist Globe ----
const CATALOGO = {
  "Fase 1 - Passagem de Cabos":[
    "Passagem de fios C.A.","Passagem de fios C.C.","Cabos de baterias",
    "Cabos do inversor","Cabos do solar","Cabos sensores","Cabo TV/Antena"
  ],
  "Fase 2 - Ligações":[
    "Tomadas 110V","Tomadas USB","Iluminação interna","Iluminação externa",
    "Toldo elétrico","Slide-out","Ar condicionado","Aquecedor",
    "Bomba d'água","Geladeira","Ventilador de teto","Step elétrico"
  ],
  "Fase 3 - Central e Painel":[
    "Instalação central eletro-eletrônica","Instalação inversor","Controlador solar",
    "Baterias de serviço","Quadro de fusíveis","Botões painel comando",
    "Display monitoramento","Teste geral C.A.","Teste geral C.C.","Conferência final"
  ]
};
const STORAGE_KEY = "globe_eletrica_v1";
let DATA = JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");
let editId = null;

const COLORS={ok:'#22c55e',warn:'#f59e0b',bad:'#ef4444',info:'#06b6d4',accent:'#3b82f6',purple:'#a855f7',muted:'#64748b'};
const STATUS_COLORS={'Concluído':COLORS.ok,'Em andamento':COLORS.info,'Atrasado':COLORS.bad,'Não iniciado':COLORS.muted};
const FASE_COLORS={'Fase 1 - Passagem de Cabos':COLORS.accent,'Fase 2 - Ligações':COLORS.purple,'Fase 3 - Central e Painel':COLORS.info};

Chart.defaults.color='#8da0c7';
Chart.defaults.borderColor='rgba(255,255,255,0.05)';

// ---- Setup ----
function fillFases(){
  const f=document.getElementById('i-fase');f.innerHTML='';
  Object.keys(CATALOGO).forEach(k=>{const o=document.createElement('option');o.value=k;o.textContent=k;f.appendChild(o)});
  fillTarefas();
}
function fillTarefas(){
  const fase=document.getElementById('i-fase').value;
  const t=document.getElementById('i-tarefa');t.innerHTML='';
  (CATALOGO[fase]||[]).forEach(x=>{const o=document.createElement('option');o.value=x;o.textContent=x;t.appendChild(o)});
}
document.getElementById('i-fase').addEventListener('change',fillTarefas);
fillFases();

// Tabs
document.querySelectorAll('.tab').forEach(t=>t.onclick=()=>{
  document.querySelectorAll('.tab').forEach(x=>x.classList.remove('active'));
  document.querySelectorAll('.view').forEach(x=>x.classList.remove('active'));
  t.classList.add('active');
  document.getElementById('view-'+t.dataset.view).classList.add('active');
  if(t.dataset.view==='dashboard')renderDashboard();
});

// ---- Toast ----
function toast(msg,err){const t=document.getElementById('toast');t.textContent=msg;t.className='toast show'+(err?' err':'');setTimeout(()=>t.className='toast',2200)}

// ---- CRUD ----
function persist(){localStorage.setItem(STORAGE_KEY,JSON.stringify(DATA));refreshSuggestions();renderTable();}
function uid(){return Date.now().toString(36)+Math.random().toString(36).slice(2,7)}

function calcAtraso(r){
  if(r.real_fim && r.prev_fim){
    return Math.round((new Date(r.real_fim)-new Date(r.prev_fim))/86400000);
  }
  return null;
}
function autoStatus(r){
  // if user picked status, keep; else infer
  if(r.status)return r.status;
  if(r.real_fim)return 'Concluído';
  if(r.real_ini)return 'Em andamento';
  return 'Não iniciado';
}

function saveTask(){
  const veic=document.getElementById('i-veiculo').value.trim();
  if(!veic){toast('Informe o veículo',true);return;}
  const obj={
    id: editId || uid(),
    veiculo: veic,
    fase: document.getElementById('i-fase').value,
    tarefa: document.getElementById('i-tarefa').value,
    responsavel: document.getElementById('i-responsavel').value.trim()||'—',
    prev_ini: document.getElementById('i-prev-ini').value||null,
    prev_fim: document.getElementById('i-prev-fim').value||null,
    real_ini: document.getElementById('i-real-ini').value||null,
    real_fim: document.getElementById('i-real-fim').value||null,
    status: document.getElementById('i-status').value,
    rubrica: document.getElementById('i-rubrica').value==='sim',
    obs: document.getElementById('i-obs').value.trim()
  };
  obj.categoria = obj.fase.split(' - ')[1] || obj.fase;
  obj.atraso_dias = calcAtraso(obj);

  if(editId){
    DATA = DATA.map(x=>x.id===editId?obj:x);
    toast('Tarefa atualizada');
  }else{
    DATA.push(obj);toast('Tarefa adicionada');
  }
  editId=null;document.getElementById('edit-info').textContent='';
  persist();resetForm(true);
}

function resetForm(keepVeiculo){
  if(!keepVeiculo)document.getElementById('i-veiculo').value='';
  ['i-prev-ini','i-prev-fim','i-real-ini','i-real-fim','i-obs'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('i-status').value='Não iniciado';
  document.getElementById('i-rubrica').value='nao';
  editId=null;document.getElementById('edit-info').textContent='';
}

function editTask(id){
  const r=DATA.find(x=>x.id===id);if(!r)return;
  editId=id;
  document.getElementById('i-veiculo').value=r.veiculo;
  document.getElementById('i-fase').value=r.fase;fillTarefas();
  document.getElementById('i-tarefa').value=r.tarefa;
  document.getElementById('i-responsavel').value=r.responsavel;
  document.getElementById('i-prev-ini').value=r.prev_ini||'';
  document.getElementById('i-prev-fim').value=r.prev_fim||'';
  document.getElementById('i-real-ini').value=r.real_ini||'';
  document.getElementById('i-real-fim').value=r.real_fim||'';
  document.getElementById('i-status').value=r.status;
  document.getElementById('i-rubrica').value=r.rubrica?'sim':'nao';
  document.getElementById('i-obs').value=r.obs||'';
  document.getElementById('edit-info').textContent='Editando: '+r.veiculo+' / '+r.tarefa;
  window.scrollTo({top:0,behavior:'smooth'});
}
function delTask(id){if(!confirm('Excluir esta tarefa?'))return;DATA=DATA.filter(x=>x.id!==id);persist();toast('Excluída');}

function clearAll(){if(!confirm('Apagar TODOS os dados? Esta ação não pode ser desfeita.'))return;DATA=[];persist();toast('Tudo limpo');}

function exportJSON(){
  const blob=new Blob([JSON.stringify(DATA,null,2)],{type:'application/json'});
  const url=URL.createObjectURL(blob);
  const a=document.createElement('a');a.href=url;a.download='globe_eletrica_'+new Date().toISOString().slice(0,10)+'.json';a.click();
  URL.revokeObjectURL(url);
}
function importJSON(e){
  const f=e.target.files[0];if(!f)return;
  const r=new FileReader();
  r.onload=()=>{try{const d=JSON.parse(r.result);if(!Array.isArray(d))throw 0;
    if(!confirm('Substituir os dados atuais por '+d.length+' registros?'))return;
    DATA=d.map(x=>({id:x.id||uid(),...x}));persist();toast('Importado');
  }catch(e){toast('Arquivo inválido',true)}};
  r.readAsText(f);e.target.value='';
}

function loadSample(){
  if(DATA.length && !confirm('Substituir os dados atuais pelos exemplos?'))return;
  const resp=['Carlos S.','Marina O.','João P.','Lucas F.','Ana R.'];
  const veics=['GLB-2026-001','GLB-2026-002','GLB-2026-003','GLB-2026-004'];
  const out=[];let day=0;
  const today=new Date('2026-06-22');
  veics.forEach((v,vi)=>{
    let cur=new Date(today);cur.setDate(cur.getDate()-60+vi*8);
    Object.entries(CATALOGO).forEach(([fase,tasks])=>{
      tasks.forEach(t=>{
        const pIni=new Date(cur);
        const pFim=new Date(cur);pFim.setDate(pFim.getDate()+1+Math.floor(Math.random()*2));
        const r=Math.random();
        const veicProg=1-vi*0.18;
        let status,rIni=null,rFim=null,atr=null;
        if(r<veicProg-0.1){
          const a=[0,0,0,1,2,3,5][Math.floor(Math.random()*7)];
          rIni=new Date(pIni);rFim=new Date(pFim);rFim.setDate(rFim.getDate()+a);
          status='Concluído';atr=a;
        }else if(r<veicProg+0.05){
          rIni=new Date(pIni);status='Em andamento';
        }else{
          status= pFim<today?'Atrasado':'Não iniciado';
        }
        const obj={id:uid(),veiculo:v,fase,tarefa:t,categoria:fase.split(' - ')[1],
          responsavel:resp[Math.floor(Math.random()*resp.length)],
          prev_ini:pIni.toISOString().slice(0,10),prev_fim:pFim.toISOString().slice(0,10),
          real_ini:rIni?rIni.toISOString().slice(0,10):null,
          real_fim:rFim?rFim.toISOString().slice(0,10):null,
          status,rubrica:status==='Concluído'&&Math.random()<0.9,atraso_dias:atr,obs:''};
        out.push(obj);
        cur=new Date(pFim);
      });
      cur.setDate(cur.getDate()+1);
    });
  });
  DATA=out;persist();toast(out.length+' registros carregados');
}

// ---- Sugestões ----
function refreshSuggestions(){
  const vs=[...new Set(DATA.map(d=>d.veiculo))].sort();
  document.getElementById('lst-veiculos').innerHTML=vs.map(v=>`<option value="${v}">`).join('');
  const rs=[...new Set(DATA.map(d=>d.responsavel).filter(x=>x&&x!=='—'))].sort();
  document.getElementById('lst-resp').innerHTML=rs.map(v=>`<option value="${v}">`).join('');
  // table filters
  const fv=document.getElementById('ft-veic'),ff=document.getElementById('ft-fase'),fs=document.getElementById('ft-status');
  const cur={v:fv.value,f:ff.value,s:fs.value};
  fv.innerHTML='<option value="">Todos veículos</option>'+vs.map(v=>`<option ${v===cur.v?'selected':''}>${v}</option>`).join('');
  ff.innerHTML='<option value="">Todas fases</option>'+Object.keys(CATALOGO).map(f=>`<option ${f===cur.f?'selected':''}>${f}</option>`).join('');
  fs.innerHTML='<option value="">Todos status</option>'+['Não iniciado','Em andamento','Concluído','Atrasado'].map(s=>`<option ${s===cur.s?'selected':''}>${s}</option>`).join('');
}

function renderTable(){
  const q=(document.getElementById('search').value||'').toLowerCase();
  const fv=document.getElementById('ft-veic').value;
  const ff=document.getElementById('ft-fase').value;
  const fs=document.getElementById('ft-status').value;
  const rows=DATA.filter(r=>{
    if(fv&&r.veiculo!==fv)return false;if(ff&&r.fase!==ff)return false;if(fs&&r.status!==fs)return false;
    if(q&&!(r.veiculo+r.tarefa+r.responsavel).toLowerCase().includes(q))return false;
    return true;
  }).sort((a,b)=>(b.prev_ini||'').localeCompare(a.prev_ini||''));
  const tb=document.getElementById('tbl-body');
  if(!rows.length){tb.innerHTML='<tr><td colspan="12" class="empty">Sem tarefas. Adicione uma acima 👆 ou clique em <b>🎲 Dados de exemplo</b>.</td></tr>';return}
  tb.innerHTML=rows.map(r=>{
    const a=r.atraso_dias;
    const aTxt=a===null||a===undefined?'-':(a>0?'+'+a+'d':(a<0?a+'d':'0'));
    const aCls=a===null?'b-muted':a<=0?'b-ok':a<=3?'b-warn':'b-bad';
    const sCls={'Concluído':'b-ok','Em andamento':'b-info','Atrasado':'b-bad','Não iniciado':'b-muted'}[r.status]||'b-muted';
    return `<tr><td>${r.veiculo}</td><td>${r.fase.split(' - ')[0]}</td><td>${r.tarefa}</td>
    <td>${r.responsavel}</td><td>${r.prev_ini||'-'}</td><td>${r.prev_fim||'-'}</td>
    <td>${r.real_ini||'-'}</td><td>${r.real_fim||'-'}</td>
    <td><span class="badge ${sCls}">${r.status}</span></td>
    <td>${r.rubrica?'✓':'—'}</td>
    <td><span class="badge ${aCls}">${aTxt}</span></td>
    <td class="row-actions"><button title="Editar" onclick="editTask('${r.id}')">✏️</button>
    <button title="Excluir" onclick="delTask('${r.id}')">🗑</button></td></tr>`;
  }).join('');
}

// ---- DASHBOARD ----
function uniq(arr){return [...new Set(arr)].sort()}
function fillSel(id,vals){
  const s=document.getElementById(id);const cur=s.value;
  s.innerHTML=s.children[0].outerHTML+vals.map(v=>`<option ${v===cur?'selected':''}>${v}</option>`).join('');
}
function setupDashFilters(){
  fillSel('f-veiculo',uniq(DATA.map(d=>d.veiculo)));
  fillSel('f-fase',uniq(DATA.map(d=>d.fase)));
  fillSel('f-categoria',uniq(DATA.map(d=>d.categoria)));
  fillSel('f-responsavel',uniq(DATA.map(d=>d.responsavel)));
  fillSel('f-status',uniq(DATA.map(d=>d.status)));
}
const DASH_FILTERS=['f-veiculo','f-fase','f-categoria','f-responsavel','f-status','f-atraso','f-rubrica','f-data-de','f-data-ate'];
DASH_FILTERS.forEach(id=>document.getElementById(id).addEventListener('change',renderDashboard));
function resetFilters(){DASH_FILTERS.forEach(id=>document.getElementById(id).value='');renderDashboard()}

function applyFilters(){
  const v=id=>document.getElementById(id).value;
  return DATA.filter(d=>{
    if(v('f-veiculo')&&d.veiculo!==v('f-veiculo'))return false;
    if(v('f-fase')&&d.fase!==v('f-fase'))return false;
    if(v('f-categoria')&&d.categoria!==v('f-categoria'))return false;
    if(v('f-responsavel')&&d.responsavel!==v('f-responsavel'))return false;
    if(v('f-status')&&d.status!==v('f-status'))return false;
    if(v('f-rubrica')){if(v('f-rubrica')==='sim'&&!d.rubrica)return false;if(v('f-rubrica')==='nao'&&d.rubrica)return false}
    if(v('f-atraso')){const a=d.atraso_dias;if(a===null||a===undefined)return false;
      const f=v('f-atraso');
      if(f==='no'&&!(a<=0))return false;if(f==='1-3'&&!(a>=1&&a<=3))return false;
      if(f==='4-7'&&!(a>=4&&a<=7))return false;if(f==='8+'&&!(a>=8))return false;}
    if(v('f-data-de')&&d.prev_ini&&d.prev_ini<v('f-data-de'))return false;
    if(v('f-data-ate')&&d.prev_ini&&d.prev_ini>v('f-data-ate'))return false;
    return true;
  });
}

const charts={};
function mk(id,cfg){if(charts[id])charts[id].destroy();const el=document.getElementById(id);if(!el)return;charts[id]=new Chart(el,cfg)}
function groupBy(rows,key){const m={};rows.forEach(r=>{(m[r[key]]=m[r[key]]||[]).push(r)});return m}

function renderDashboard(){
  setupDashFilters();
  const empty=DATA.length===0;
  document.getElementById('empty-dash').style.display=empty?'block':'none';
  document.getElementById('dash-content').style.display=empty?'none':'block';
  if(empty)return;
  const rows=applyFilters();
  renderKPIs(rows);renderBurndown(rows);renderFase(rows);renderPrevReal(rows);
  renderStatus(rows);renderStack(rows);renderCat(rows);renderResp(rows);renderRespAtraso(rows);
  renderPareto(rows);renderFaixas(rows);renderDOW(rows);renderCarga(rows);renderGantt(rows);renderAtrasoTable(rows);
}

function renderKPIs(rows){
  const total=rows.length,concl=rows.filter(r=>r.status==='Concluído').length;
  const atras=rows.filter(r=>r.status==='Atrasado').length;
  const conclRows=rows.filter(r=>r.status==='Concluído');
  const noPrazo=conclRows.filter(r=>(r.atraso_dias??0)<=0).length;
  const atrasoMed=conclRows.length?conclRows.reduce((s,r)=>s+(r.atraso_dias||0),0)/conclRows.length:0;
  const aderencia=conclRows.length?noPrazo/conclRows.length*100:0;
  const semRub=conclRows.filter(r=>!r.rubrica).length;
  const byV=groupBy(rows,'veiculo');
  const veicConcl=Object.values(byV).filter(a=>a.every(r=>r.status==='Concluído')).length;
  const lts=Object.values(byV).filter(a=>a.every(r=>r.status==='Concluído')).map(a=>{
    const i=a.map(r=>r.real_ini).filter(Boolean).sort()[0];
    const f=a.map(r=>r.real_fim).filter(Boolean).sort().slice(-1)[0];
    return i&&f?(new Date(f)-new Date(i))/86400000:null;
  }).filter(x=>x!==null);
  const lt=lts.length?lts.reduce((a,b)=>a+b,0)/lts.length:0;

  const k=[
    {label:'% Conclusão',value:total?(concl/total*100).toFixed(1)+'%':'-',hint:concl+' / '+total,cls:'ok'},
    {label:'Aderência prazo',value:aderencia.toFixed(1)+'%',hint:noPrazo+' no prazo',cls:aderencia>=70?'ok':aderencia>=50?'warn':'bad'},
    {label:'Atraso médio',value:atrasoMed.toFixed(1)+' d',hint:'em concluídas',cls:atrasoMed<=1?'ok':atrasoMed<=3?'warn':'bad'},
    {label:'Em atraso',value:atras,hint:'abertas/vencidas',cls:atras?'bad':'ok'},
    {label:'Veículos concluídos',value:veicConcl,hint:'de '+Object.keys(byV).length,cls:'info'},
    {label:'Lead time médio',value:lt.toFixed(1)+' d',hint:'Fase 1→3',cls:'purple'},
    {label:'Sem rubrica',value:semRub,hint:'falha conferência',cls:semRub?'warn':'ok'},
    {label:'Tarefas (filtro)',value:total,hint:'no recorte',cls:''}
  ];
  document.getElementById('kpis').innerHTML=k.map(x=>`<div class="kpi ${x.cls}"><div class="label">${x.label}</div><div class="value">${x.value}</div><div class="hint">${x.hint}</div></div>`).join('');
}

function renderBurndown(rows){
  const c=rows.filter(r=>r.status==='Concluído'&&r.real_fim).sort((a,b)=>a.real_fim.localeCompare(b.real_fim));
  const by={};c.forEach(r=>{by[r.real_fim]=(by[r.real_fim]||0)+1});
  const d=Object.keys(by).sort();let cum=0;const data=d.map(x=>{cum+=by[x];return{x,y:cum}});
  mk('ch-burndown',{type:'line',data:{datasets:[{label:'Acumulado',data,borderColor:COLORS.ok,backgroundColor:'rgba(34,197,94,.15)',fill:true,tension:.3,pointRadius:2}]},
    options:{maintainAspectRatio:false,scales:{x:{type:'time',time:{unit:'week'}}},plugins:{legend:{display:false}}}});
}
function renderFase(rows){
  const g=groupBy(rows,'fase');const labels=Object.keys(g);
  const pct=labels.map(l=>{const a=g[l];return a.length?a.filter(r=>r.status==='Concluído').length/a.length*100:0});
  mk('ch-fase',{type:'bar',data:{labels:labels.map(l=>l.split(' - ')[0]),datasets:[{data:pct,backgroundColor:labels.map(l=>FASE_COLORS[l]||COLORS.accent)}]},
    options:{indexAxis:'y',maintainAspectRatio:false,scales:{x:{max:100,ticks:{callback:v=>v+'%'}}},plugins:{legend:{display:false}}}});
}
function renderPrevReal(rows){
  const g=groupBy(rows,'fase');const labels=Object.keys(g).map(l=>l.split(' - ')[0]);
  mk('ch-prevreal',{type:'bar',data:{labels,datasets:[
    {label:'Previsto',data:Object.values(g).map(a=>a.length),backgroundColor:'rgba(59,130,246,.5)'},
    {label:'Realizado',data:Object.values(g).map(a=>a.filter(r=>r.status==='Concluído').length),backgroundColor:COLORS.ok}]},
    options:{maintainAspectRatio:false}});
}
function renderStatus(rows){
  const g=groupBy(rows,'status');const labels=Object.keys(g);
  mk('ch-status',{type:'pie',data:{labels,datasets:[{data:labels.map(l=>g[l].length),backgroundColor:labels.map(l=>STATUS_COLORS[l]||COLORS.muted)}]},
    options:{maintainAspectRatio:false,plugins:{legend:{position:'bottom'}}}});
}
function renderStack(rows){
  const cats=uniq(rows.map(r=>r.categoria));
  const ss=['Concluído','Em andamento','Atrasado','Não iniciado'];
  mk('ch-stack',{type:'bar',data:{labels:cats,datasets:ss.map(s=>({label:s,backgroundColor:STATUS_COLORS[s],
    data:cats.map(c=>rows.filter(r=>r.categoria===c&&r.status===s).length)}))},
    options:{maintainAspectRatio:false,scales:{x:{stacked:true},y:{stacked:true}}}});
}
function renderCat(rows){
  const g=groupBy(rows,'categoria');const labels=Object.keys(g);
  mk('ch-cat',{type:'doughnut',data:{labels,datasets:[{data:labels.map(l=>g[l].length),
    backgroundColor:[COLORS.accent,COLORS.purple,COLORS.info,COLORS.ok,COLORS.warn]}]},
    options:{maintainAspectRatio:false,plugins:{legend:{position:'bottom'}}}});
}
function renderResp(rows){
  const g=groupBy(rows.filter(r=>r.status==='Concluído'),'responsavel');
  const labels=Object.keys(g).sort((a,b)=>g[b].length-g[a].length);
  mk('ch-resp',{type:'bar',data:{labels,datasets:[{data:labels.map(l=>g[l].length),backgroundColor:COLORS.accent}]},
    options:{indexAxis:'y',maintainAspectRatio:false,plugins:{legend:{display:false}}}});
}
function renderRespAtraso(rows){
  const c=rows.filter(r=>r.status==='Concluído');const g=groupBy(c,'responsavel');
  const arr=Object.entries(g).map(([l,a])=>({l,v:a.reduce((s,r)=>s+(r.atraso_dias||0),0)/(a.length||1)})).sort((a,b)=>b.v-a.v);
  mk('ch-resp-atraso',{type:'bar',data:{labels:arr.map(x=>x.l),datasets:[{data:arr.map(x=>x.v),
    backgroundColor:arr.map(x=>x.v<=1?COLORS.ok:x.v<=3?COLORS.warn:COLORS.bad)}]},
    options:{indexAxis:'y',maintainAspectRatio:false,plugins:{legend:{display:false}}}});
}
function renderPareto(rows){
  const c=rows.filter(r=>r.status==='Concluído'&&(r.atraso_dias||0)>0);
  const g={};c.forEach(r=>{g[r.tarefa]=(g[r.tarefa]||0)+r.atraso_dias});
  const arr=Object.entries(g).sort((a,b)=>b[1]-a[1]).slice(0,12);
  const tot=arr.reduce((s,x)=>s+x[1],0);let cum=0;
  const cumPct=arr.map(x=>{cum+=x[1];return tot?cum/tot*100:0});
  mk('ch-pareto',{data:{labels:arr.map(x=>x[0]),datasets:[
    {type:'bar',label:'Dias',data:arr.map(x=>x[1]),backgroundColor:COLORS.bad,yAxisID:'y'},
    {type:'line',label:'% acum.',data:cumPct,borderColor:COLORS.warn,yAxisID:'y1',tension:.2}]},
    options:{maintainAspectRatio:false,scales:{y:{position:'left'},y1:{position:'right',max:100,grid:{display:false},ticks:{callback:v=>v+'%'}}}}});
}
function renderFaixas(rows){
  const c=rows.filter(r=>r.status==='Concluído');const b={'No prazo':0,'1-3 d':0,'4-7 d':0,'8+ d':0};
  c.forEach(r=>{const a=r.atraso_dias||0;if(a<=0)b['No prazo']++;else if(a<=3)b['1-3 d']++;else if(a<=7)b['4-7 d']++;else b['8+ d']++});
  mk('ch-faixas',{type:'doughnut',data:{labels:Object.keys(b),datasets:[{data:Object.values(b),
    backgroundColor:[COLORS.ok,COLORS.info,COLORS.warn,COLORS.bad]}]},
    options:{maintainAspectRatio:false,plugins:{legend:{position:'bottom'}}}});
}
function renderDOW(rows){
  const d=['Dom','Seg','Ter','Qua','Qui','Sex','Sáb'];const c=[0,0,0,0,0,0,0];
  rows.filter(r=>r.status==='Concluído'&&r.real_fim&&(r.atraso_dias||0)>0).forEach(r=>c[new Date(r.real_fim).getDay()]++);
  mk('ch-dow',{type:'bar',data:{labels:d,datasets:[{data:c,backgroundColor:COLORS.warn}]},
    options:{maintainAspectRatio:false,plugins:{legend:{display:false}}}});
}
function renderCarga(rows){
  const a=rows.filter(r=>r.status!=='Concluído');const g=groupBy(a,'responsavel');
  const labels=Object.keys(g).sort((x,y)=>g[y].length-g[x].length);
  mk('ch-carga',{type:'bar',data:{labels,datasets:[{data:labels.map(l=>g[l].length),backgroundColor:COLORS.purple}]},
    options:{maintainAspectRatio:false,plugins:{legend:{display:false}}}});
}
function renderGantt(rows){
  const byV=groupBy(rows,'veiculo');const veics=Object.keys(byV).sort();
  let min=Infinity,max=-Infinity;
  rows.forEach(r=>{if(r.prev_ini){const a=+new Date(r.prev_ini);if(a<min)min=a}
    if(r.prev_fim){const b=+new Date(r.prev_fim);if(b>max)max=b}
    if(r.real_fim){const c=+new Date(r.real_fim);if(c>max)max=c}});
  const el=document.getElementById('gantt');
  if(!isFinite(min)||max<=min){el.innerHTML='<div class="empty">Sem datas previstas para montar o Gantt.</div>';return;}
  const span=max-min;let html='';
  veics.forEach(v=>{
    const fs=groupBy(byV[v],'fase');let bars='';
    Object.entries(fs).forEach(([fase,arr])=>{
      const pi=arr.map(r=>r.prev_ini).filter(Boolean).map(d=>+new Date(d));
      const pf=arr.map(r=>r.prev_fim).filter(Boolean).map(d=>+new Date(d));
      if(!pi.length||!pf.length)return;
      const a=Math.min(...pi),b=Math.max(...pf);
      const left=(a-min)/span*100,w=(b-a)/span*100;
      bars+=`<div class="gantt-bar" style="left:${left}%;width:${w}%;background:${FASE_COLORS[fase]||COLORS.accent}" title="${fase}"></div>`;
      const rf=arr.map(r=>r.real_fim).filter(Boolean).map(d=>+new Date(d));
      if(rf.length){const r=Math.max(...rf);if(r>b){const ex=(r-b)/span*100;bars+=`<div class="gantt-bar" style="left:${left+w}%;width:${ex}%;background:${COLORS.bad};opacity:.85" title="Atraso"></div>`}}
    });
    html+=`<div class="gantt-row"><div>${v}</div><div class="gantt-bar-track">${bars}</div></div>`;
  });
  el.innerHTML=html;
}
function renderAtrasoTable(rows){
  const a=rows.filter(r=>r.status==='Atrasado'||(r.status==='Concluído'&&(r.atraso_dias||0)>0))
    .sort((a,b)=>(b.atraso_dias||999)-(a.atraso_dias||0)).slice(0,100);
  const tb=document.querySelector('#tbl-atraso tbody');
  tb.innerHTML=a.length?a.map(r=>{
    const cls=r.status==='Atrasado'?'b-bad':(r.atraso_dias||0)>3?'b-warn':'b-info';
    return `<tr><td>${r.veiculo}</td><td>${r.fase.split(' - ')[0]}</td><td>${r.tarefa}</td><td>${r.responsavel}</td>
    <td>${r.prev_fim||'-'}</td><td>${r.real_fim||'-'}</td><td>${r.atraso_dias??'-'}</td>
    <td><span class="badge ${cls}">${r.status}</span></td></tr>`;
  }).join(''):'<tr><td colspan="8" class="empty">Nenhuma tarefa em atraso 🎉</td></tr>';
}

// ---- Init ----
refreshSuggestions();renderTable();
</script>
</body></html>
