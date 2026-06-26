
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Dashboard Fase Elétrica - Globe (com Manutenções)</title>
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
.tabs{display:flex;gap:6px;padding:0 28px;background:var(--panel);border-bottom:1px solid var(--border);flex-wrap:wrap}
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
    <button class="btn ghost" onclick="exportarJSON()">⬇ Exportar JSON</button>
    <button class="btn ghost" onclick="document.getElementById('imp').click()">⬆ Importar</button>
    <input id="imp" type="file" accept=".json" hidden onchange="importarJSON(event)">
    <button class="btn ok" onclick="carregarExemplos()">🎲 Dados de exemplo</button>
    <button class="btn danger" onclick="limparTudo()">🗑 Limpar tudo</button>
  </div>
</header>

<div class="tabs">
  <div class="tab active" onclick="trocarAba('entrada',this)">📝 Entrada de Dados</div>
  <div class="tab" onclick="trocarAba('dashboard',this)">📊 Dashboard</div>
  <div class="tab" onclick="trocarAba('manut',this)">🔧 Manutenções</div>
  <div class="tab" onclick="trocarAba('ajuda',this)">❓ Como usar</div>
</div>

<div class="container">

<!-- ============ ENTRADA ============ -->
<section id="view-entrada" class="view active">
  <div class="formgrid">
    <label>Veículo (chassi/código)
      <input id="f-veiculo" placeholder="ex: GLB-0123">
    </label>
    <label>Fase
      <select id="f-fase">
        <option>Fase 1</option><option>Fase 2</option><option>Fase 3</option>
      </select>
    </label>
    <label>Tarefa
      <input id="f-tarefa" placeholder="ex: Instalação chicote">
    </label>
    <label>Responsável
      <input id="f-resp" placeholder="ex: João Silva">
    </label>
    <label>Previsto - início <input id="f-pi" type="date"></label>
    <label>Previsto - fim <input id="f-pf" type="date"></label>
    <label>Real - início <input id="f-ri" type="date"></label>
    <label>Real - fim <input id="f-rf" type="date"></label>
    <label>Status
      <select id="f-status">
        <option>Não iniciado</option><option>Em andamento</option>
        <option>Concluído</option><option>Atrasado</option>
      </select>
    </label>
    <label>Rubrica/conferência
      <select id="f-rub"><option>Não</option><option>Sim</option></select>
    </label>
    <label class="full">Observação (opcional)
      <textarea id="f-obs" rows="2"></textarea>
    </label>
    <div class="full actions">
      <button class="btn" onclick="salvarTarefa()">💾 Salvar tarefa</button>
      <button class="btn ghost" onclick="limparFormTarefa()">Limpar campos</button>
      <input id="edit-id" hidden>
    </div>
  </div>

  <div class="card">
    <div class="toolbar">
      <input id="lf-veic" placeholder="Buscar veículo..." oninput="renderTarefas()">
      <select id="lf-fase" onchange="renderTarefas()"><option value="">Todas fases</option><option>Fase 1</option><option>Fase 2</option><option>Fase 3</option></select>
      <select id="lf-status" onchange="renderTarefas()"><option value="">Todos status</option><option>Não iniciado</option><option>Em andamento</option><option>Concluído</option><option>Atrasado</option></select>
    </div>
    <div class="scroll">
      <table><thead><tr>
        <th>Veículo</th><th>Fase</th><th>Tarefa</th><th>Responsável</th>
        <th>Prev. ini</th><th>Prev. fim</th><th>Real ini</th><th>Real fim</th>
        <th>Status</th><th>Rubrica</th><th>Atraso</th><th></th>
      </tr></thead><tbody id="tbody-tarefas"></tbody></table>
    </div>
  </div>
</section>

<!-- ============ DASHBOARD ============ -->
<section id="view-dashboard" class="view">
  <div id="empty-dash" class="empty card" style="display:none">
    Nenhum dado ainda. Vá em <b>📝 Entrada de Dados</b> ou clique em <b>🎲 Dados de exemplo</b>.
  </div>
  <div id="dash-content">
    <div class="kpis" id="kpis"></div>
    <div class="grid">
      <div class="card c-6"><h3>🚦 Status Geral</h3><div class="chart-wrap"><canvas id="ch-status"></canvas></div></div>
      <div class="card c-6"><h3>🎯 % por Fase</h3><div class="chart-wrap"><canvas id="ch-fase"></canvas></div></div>
      <div class="card c-8"><h3>👷 Ranking Responsáveis</h3><div class="chart-wrap"><canvas id="ch-resp"></canvas></div></div>
      <div class="card c-4"><h3>🪣 Faixas de atraso</h3><div class="chart-wrap"><canvas id="ch-faixas"></canvas></div></div>
      <div class="card c-12"><h3>⚠️ Tarefas em atraso</h3>
        <div class="scroll"><table><thead><tr>
          <th>Veículo</th><th>Fase</th><th>Tarefa</th><th>Responsável</th><th>Prev. fim</th><th>Atraso (d)</th><th>Status</th>
        </tr></thead><tbody id="tbl-atraso"></tbody></table></div>
      </div>
    </div>
  </div>
</section>

<!-- ============ MANUTENÇÕES ============ -->
<section id="view-manut" class="view">
  <div class="formgrid">
    <label>Veículo (chassi/placa/código)
      <input id="m-veiculo" placeholder="ex: GLB-0123">
    </label>
    <label>Tipo de manutenção
      <select id="m-tipo">
        <option>Preventiva</option><option>Corretiva</option>
        <option>Preditiva</option><option>Revisão</option><option>Inspeção</option>
      </select>
    </label>
    <label>Sistema / componente
      <select id="m-sistema">
        <option>Elétrico</option><option>Mecânico</option><option>Hidráulico</option>
        <option>Pneumático</option><option>Funilaria</option><option>Pintura</option><option>Outros</option>
      </select>
    </label>
    <label>Responsável <input id="m-resp" placeholder="ex: João Silva"></label>
    <label>Data de entrada <input id="m-entrada" type="date"></label>
    <label>Saída prevista <input id="m-saidaPrev" type="date"></label>
    <label>Saída real <input id="m-saidaReal" type="date"></label>
    <label>Prioridade
      <select id="m-prio">
        <option>Baixa</option><option selected>Média</option><option>Alta</option><option>Crítica</option>
      </select>
    </label>
    <label>Status
      <select id="m-status">
        <option>Aguardando</option><option>Em manutenção</option>
        <option>Aguardando peça</option><option>Concluído</option><option>Cancelado</option>
      </select>
    </label>
    <label>Custo estimado (R$) <input id="m-custo" type="number" step="0.01" min="0" placeholder="0,00"></label>
    <label class="full">Descrição do serviço / observação
      <textarea id="m-obs" rows="2" placeholder="Detalhes, peças trocadas, diagnóstico..."></textarea>
    </label>
    <div class="full actions">
      <button class="btn" onclick="salvarManut()">💾 Salvar manutenção</button>
      <button class="btn ghost" onclick="limparFormManut()">Limpar campos</button>
      <input id="edit-mid" hidden>
    </div>
  </div>

  <div id="manut-kpis" class="kpis"></div>

  <div class="grid">
    <div class="card c-6"><h3>📊 Status das manutenções</h3><div class="chart-wrap"><canvas id="mch-status"></canvas></div></div>
    <div class="card c-6"><h3>🔧 Por tipo</h3><div class="chart-wrap"><canvas id="mch-tipo"></canvas></div></div>
    <div class="card c-6"><h3>⚙️ Sistema / componente</h3><div class="chart-wrap"><canvas id="mch-sistema"></canvas></div></div>
    <div class="card c-6"><h3>🚨 Prioridade</h3><div class="chart-wrap"><canvas id="mch-prio"></canvas></div></div>
    <div class="card c-12"><h3>📋 Manutenções cadastradas</h3>
      <div class="toolbar">
        <input id="mf-veic" placeholder="Buscar veículo..." oninput="renderManut()">
        <select id="mf-status" onchange="renderManut()">
          <option value="">Todos status</option>
          <option>Aguardando</option><option>Em manutenção</option>
          <option>Aguardando peça</option><option>Concluído</option><option>Cancelado</option>
        </select>
        <select id="mf-tipo" onchange="renderManut()">
          <option value="">Todos tipos</option>
          <option>Preventiva</option><option>Corretiva</option>
          <option>Preditiva</option><option>Revisão</option><option>Inspeção</option>
        </select>
        <select id="mf-prio" onchange="renderManut()">
          <option value="">Todas prioridades</option>
          <option>Baixa</option><option>Média</option><option>Alta</option><option>Crítica</option>
        </select>
      </div>
      <div class="scroll">
        <table><thead><tr>
          <th>Veículo</th><th>Tipo</th><th>Sistema</th><th>Responsável</th>
          <th>Entrada</th><th>Saída prev.</th><th>Saída real</th>
          <th>Prioridade</th><th>Status</th><th>Dias</th><th>Custo</th><th></th>
        </tr></thead><tbody id="tbody-manut"></tbody></table>
      </div>
    </div>
  </div>
</section>

<!-- ============ AJUDA ============ -->
<section id="view-ajuda" class="view">
  <div class="card">
    <h3>Como usar este dashboard</h3>
    <ul style="line-height:1.8;color:var(--muted)">
      <li><b>Entrada de dados:</b> preencha o formulário com cada tarefa do checklist da fase elétrica.</li>
      <li><b>Manutenções:</b> aba separada para registrar veículos em manutenção (entrada, saída prevista, responsável, status etc.).</li>
      <li><b>Persistência:</b> tudo é salvo automaticamente no seu navegador (localStorage). Tarefas e manutenções ficam em chaves separadas, sem conflito.</li>
      <li><b>Editar/excluir:</b> use ✏️ e 🗑 nas tabelas.</li>
      <li><b>Backup:</b> Exportar/Importar JSON inclui tarefas + manutenções.</li>
      <li><b>Dashboard:</b> KPIs e gráficos da fase elétrica; a aba de Manutenções tem seus próprios KPIs e gráficos.</li>
    </ul>
  </div>
</section>

</div>

<div id="toast" class="toast"></div>
<footer>Dados salvos localmente neste navegador · Faça exportações periódicas como backup</footer>

<script>
const K_TAR='tarefas_globe_v1', K_MAN='manutencoes_globe_v1';
let tarefas = JSON.parse(localStorage.getItem(K_TAR)||'[]');
let manut   = JSON.parse(localStorage.getItem(K_MAN)||'[]');
let charts={}, mcharts={};

const saveT=()=>localStorage.setItem(K_TAR,JSON.stringify(tarefas));
const saveM=()=>localStorage.setItem(K_MAN,JSON.stringify(manut));
const uid=()=>Date.now().toString(36)+Math.random().toString(36).slice(2,7);
function toast(msg,err){const t=document.getElementById('toast');t.textContent=msg;t.className='toast show'+(err?' err':'');setTimeout(()=>t.className='toast',2200);}

function trocarAba(v,el){
  document.querySelectorAll('.view').forEach(x=>x.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(x=>x.classList.remove('active'));
  document.getElementById('view-'+v).classList.add('active');
  el.classList.add('active');
  if(v==='entrada') renderTarefas();
  if(v==='dashboard') renderDashboard();
  if(v==='manut'){ renderManut(); renderManutDash(); }
}

/* ============ TAREFAS ============ */
function limparFormTarefa(){
  ['f-veiculo','f-tarefa','f-resp','f-pi','f-pf','f-ri','f-rf','f-obs'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('f-fase').selectedIndex=0;
  document.getElementById('f-status').selectedIndex=0;
  document.getElementById('f-rub').selectedIndex=0;
  document.getElementById('edit-id').value='';
}
function salvarTarefa(){
  const v=document.getElementById('f-veiculo').value.trim();
  const tr=document.getElementById('f-tarefa').value.trim();
  if(!v||!tr){toast('Veículo e tarefa são obrigatórios',true);return;}
  const r={
    id:document.getElementById('edit-id').value||uid(),
    veiculo:v, fase:document.getElementById('f-fase').value, tarefa:tr,
    responsavel:document.getElementById('f-resp').value.trim(),
    pi:document.getElementById('f-pi').value, pf:document.getElementById('f-pf').value,
    ri:document.getElementById('f-ri').value, rf:document.getElementById('f-rf').value,
    status:document.getElementById('f-status').value,
    rubrica:document.getElementById('f-rub').value,
    obs:document.getElementById('f-obs').value.trim()
  };
  const i=tarefas.findIndex(x=>x.id===r.id);
  if(i>=0) tarefas[i]=r; else tarefas.push(r);
  saveT(); limparFormTarefa(); renderTarefas(); toast('Tarefa salva ✓');
}
function editarT(id){
  const r=tarefas.find(x=>x.id===id);if(!r)return;
  document.getElementById('edit-id').value=r.id;
  document.getElementById('f-veiculo').value=r.veiculo;
  document.getElementById('f-fase').value=r.fase;
  document.getElementById('f-tarefa').value=r.tarefa;
  document.getElementById('f-resp').value=r.responsavel||'';
  document.getElementById('f-pi').value=r.pi||'';document.getElementById('f-pf').value=r.pf||'';
  document.getElementById('f-ri').value=r.ri||'';document.getElementById('f-rf').value=r.rf||'';
  document.getElementById('f-status').value=r.status;
  document.getElementById('f-rub').value=r.rubrica||'Não';
  document.getElementById('f-obs').value=r.obs||'';
  window.scrollTo({top:0,behavior:'smooth'});
}
function excluirT(id){if(!confirm('Excluir esta tarefa?'))return;tarefas=tarefas.filter(x=>x.id!==id);saveT();renderTarefas();toast('Excluído');}
function diasEntre(a,b){if(!a||!b)return null;return Math.round((new Date(b)-new Date(a))/86400000);}
function atrasoT(r){
  if(!r.pf) return 0;
  const ref = r.status==='Concluído' ? (r.rf||new Date().toISOString().slice(0,10)) : new Date().toISOString().slice(0,10);
  const d = diasEntre(r.pf, ref); return d>0?d:0;
}
function badgeStatusT(s){const m={'Não iniciado':'b-muted','Em andamento':'b-info','Concluído':'b-ok','Atrasado':'b-bad'};return `<span class="badge ${m[s]||'b-muted'}">${s}</span>`;}

function renderTarefas(){
  const fv=document.getElementById('lf-veic').value.toLowerCase();
  const ff=document.getElementById('lf-fase').value;
  const fs=document.getElementById('lf-status').value;
  const list=tarefas.filter(r=>(!fv||r.veiculo.toLowerCase().includes(fv))&&(!ff||r.fase===ff)&&(!fs||r.status===fs));
  const tb=document.getElementById('tbody-tarefas');
  if(!list.length){tb.innerHTML='<tr><td colspan="12" class="empty">Sem registros</td></tr>';return;}
  tb.innerHTML=list.map(r=>{const a=atrasoT(r);return `<tr>
    <td><b>${r.veiculo}</b></td><td>${r.fase}</td><td>${r.tarefa}</td><td>${r.responsavel||'-'}</td>
    <td>${r.pi||'-'}</td><td>${r.pf||'-'}</td><td>${r.ri||'-'}</td><td>${r.rf||'-'}</td>
    <td>${badgeStatusT(r.status)}</td><td>${r.rubrica==='Sim'?'<span class="badge b-ok">Sim</span>':'<span class="badge b-muted">Não</span>'}</td>
    <td>${a>0?`<span class="badge b-bad">+${a}d</span>`:'<span class="badge b-ok">0</span>'}</td>
    <td class="row-actions"><button onclick="editarT('${r.id}')">✏️</button><button onclick="excluirT('${r.id}')">🗑</button></td>
  </tr>`;}).join('');
}

function renderDashboard(){
  if(!tarefas.length){document.getElementById('empty-dash').style.display='block';document.getElementById('dash-content').style.display='none';return;}
  document.getElementById('empty-dash').style.display='none';document.getElementById('dash-content').style.display='block';

  const total=tarefas.length;
  const concl=tarefas.filter(r=>r.status==='Concluído').length;
  const atrasadas=tarefas.filter(r=>atrasoT(r)>0).length;
  const semRub=tarefas.filter(r=>r.rubrica!=='Sim').length;
  const atrasoMed=tarefas.reduce((s,r)=>s+atrasoT(r),0)/(total||1);
  const veicCompl=[...new Set(tarefas.map(r=>r.veiculo))].filter(v=>{
    const ts=tarefas.filter(t=>t.veiculo===v); return ts.every(t=>t.status==='Concluído');
  }).length;

  document.getElementById('kpis').innerHTML=
    kpi('% Conclusão',(concl/total*100).toFixed(0)+'%',concl+'/'+total,'ok')+
    kpi('Atrasadas',atrasadas,'tarefas com atraso',atrasadas?'bad':'ok')+
    kpi('Atraso médio',atrasoMed.toFixed(1)+' d','vs. previsto','warn')+
    kpi('Sem rubrica',semRub,'pendentes de conferência','warn')+
    kpi('Veículos concluídos',veicCompl,'todas tarefas OK','info')+
    kpi('Total de tarefas',total,'no sistema','purple');

  Object.values(charts).forEach(c=>c.destroy());charts={};
  const cor=['#3b82f6','#22c55e','#f59e0b','#ef4444','#06b6d4','#a855f7','#94a3b8'];
  const opt={plugins:{legend:{labels:{color:'#e6ecff',font:{size:11}}}},scales:{x:{ticks:{color:'#8da0c7'},grid:{color:'#243056'}},y:{ticks:{color:'#8da0c7'},grid:{color:'#243056'}}}};
  const pie={plugins:{legend:{labels:{color:'#e6ecff',font:{size:11}}}}};
  const g=(k)=>tarefas.reduce((m,r)=>{m[r[k]]=(m[r[k]]||0)+1;return m;},{});
  const gs=g('status');
  charts.s=new Chart(document.getElementById('ch-status'),{type:'doughnut',data:{labels:Object.keys(gs),datasets:[{data:Object.values(gs),backgroundColor:cor}]},options:pie});

  const fases=['Fase 1','Fase 2','Fase 3'];
  const perc=fases.map(f=>{const t=tarefas.filter(r=>r.fase===f);return t.length?(t.filter(r=>r.status==='Concluído').length/t.length*100):0;});
  charts.f=new Chart(document.getElementById('ch-fase'),{type:'bar',data:{labels:fases,datasets:[{label:'% Concluído',data:perc,backgroundColor:'#22c55e'}]},options:{...opt,scales:{...opt.scales,y:{...opt.scales.y,max:100}}}});

  const rm={};tarefas.forEach(r=>{if(!r.responsavel)return;rm[r.responsavel]=(rm[r.responsavel]||0)+1;});
  const rs=Object.entries(rm).sort((a,b)=>b[1]-a[1]);
  charts.r=new Chart(document.getElementById('ch-resp'),{type:'bar',data:{labels:rs.map(x=>x[0]),datasets:[{label:'Tarefas',data:rs.map(x=>x[1]),backgroundColor:'#3b82f6'}]},options:{...opt,indexAxis:'y'}});

  const faixas={'No prazo':0,'1-3 d':0,'4-7 d':0,'8+ d':0};
  tarefas.forEach(r=>{const a=atrasoT(r);if(a<=0)faixas['No prazo']++;else if(a<=3)faixas['1-3 d']++;else if(a<=7)faixas['4-7 d']++;else faixas['8+ d']++;});
  charts.fx=new Chart(document.getElementById('ch-faixas'),{type:'doughnut',data:{labels:Object.keys(faixas),datasets:[{data:Object.values(faixas),backgroundColor:['#22c55e','#06b6d4','#f59e0b','#ef4444']}]},options:pie});

  const atr=tarefas.filter(r=>atrasoT(r)>0).sort((a,b)=>atrasoT(b)-atrasoT(a));
  document.getElementById('tbl-atraso').innerHTML = atr.length? atr.map(r=>`<tr>
    <td><b>${r.veiculo}</b></td><td>${r.fase}</td><td>${r.tarefa}</td><td>${r.responsavel||'-'}</td>
    <td>${r.pf||'-'}</td><td><span class="badge b-bad">+${atrasoT(r)}</span></td><td>${badgeStatusT(r.status)}</td>
  </tr>`).join('') : '<tr><td colspan="7" class="empty">Nenhuma tarefa em atraso 🎉</td></tr>';
}

/* ============ MANUTENÇÕES ============ */
function limparFormManut(){
  ['m-veiculo','m-resp','m-entrada','m-saidaPrev','m-saidaReal','m-custo','m-obs'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('m-tipo').selectedIndex=0;
  document.getElementById('m-sistema').selectedIndex=0;
  document.getElementById('m-prio').value='Média';
  document.getElementById('m-status').selectedIndex=0;
  document.getElementById('edit-mid').value='';
}
function salvarManut(){
  const v=document.getElementById('m-veiculo').value.trim();
  const ent=document.getElementById('m-entrada').value;
  const resp=document.getElementById('m-resp').value.trim();
  if(!v||!ent||!resp){toast('Preencha veículo, entrada e responsável',true);return;}
  const r={
    id:document.getElementById('edit-mid').value||uid(),
    veiculo:v, tipo:document.getElementById('m-tipo').value,
    sistema:document.getElementById('m-sistema').value, responsavel:resp,
    entrada:ent, saidaPrev:document.getElementById('m-saidaPrev').value,
    saidaReal:document.getElementById('m-saidaReal').value,
    prioridade:document.getElementById('m-prio').value,
    status:document.getElementById('m-status').value,
    custo:parseFloat(document.getElementById('m-custo').value)||0,
    obs:document.getElementById('m-obs').value.trim()
  };
  const i=manut.findIndex(x=>x.id===r.id);
  if(i>=0) manut[i]=r; else manut.push(r);
  saveM(); limparFormManut(); renderManut(); renderManutDash(); toast('Manutenção salva ✓');
}
function editarM(id){
  const r=manut.find(x=>x.id===id);if(!r)return;
  document.getElementById('edit-mid').value=r.id;
  document.getElementById('m-veiculo').value=r.veiculo;
  document.getElementById('m-tipo').value=r.tipo;
  document.getElementById('m-sistema').value=r.sistema;
  document.getElementById('m-resp').value=r.responsavel;
  document.getElementById('m-entrada').value=r.entrada;
  document.getElementById('m-saidaPrev').value=r.saidaPrev||'';
  document.getElementById('m-saidaReal').value=r.saidaReal||'';
  document.getElementById('m-prio').value=r.prioridade;
  document.getElementById('m-status').value=r.status;
  document.getElementById('m-custo').value=r.custo||'';
  document.getElementById('m-obs').value=r.obs||'';
  window.scrollTo({top:0,behavior:'smooth'});
}
function excluirM(id){if(!confirm('Excluir esta manutenção?'))return;manut=manut.filter(x=>x.id!==id);saveM();renderManut();renderManutDash();toast('Excluído');}
function diasParado(r){const fim=r.status==='Concluído'&&r.saidaReal?new Date(r.saidaReal):new Date();return diasEntre(r.entrada,fim.toISOString().slice(0,10));}
function atrasoM(r){if(!r.saidaPrev)return 0;const ref=r.status==='Concluído'?(r.saidaReal||new Date().toISOString().slice(0,10)):new Date().toISOString().slice(0,10);const d=diasEntre(r.saidaPrev,ref);return d>0?d:0;}
function badgeStatusM(s){const m={'Aguardando':'b-muted','Em manutenção':'b-info','Aguardando peça':'b-warn','Concluído':'b-ok','Cancelado':'b-bad'};return `<span class="badge ${m[s]||'b-muted'}">${s}</span>`;}
function badgePrio(p){const m={'Baixa':'b-muted','Média':'b-info','Alta':'b-warn','Crítica':'b-bad'};return `<span class="badge ${m[p]||'b-muted'}">${p}</span>`;}

function renderManut(){
  const fv=document.getElementById('mf-veic').value.toLowerCase();
  const fs=document.getElementById('mf-status').value;
  const ft=document.getElementById('mf-tipo').value;
  const fp=document.getElementById('mf-prio').value;
  const list=manut.filter(r=>(!fv||r.veiculo.toLowerCase().includes(fv))&&(!fs||r.status===fs)&&(!ft||r.tipo===ft)&&(!fp||r.prioridade===fp))
    .sort((a,b)=>(b.entrada||'').localeCompare(a.entrada||''));
  const tb=document.getElementById('tbody-manut');
  if(!list.length){tb.innerHTML='<tr><td colspan="12" class="empty">Sem registros</td></tr>';return;}
  tb.innerHTML=list.map(r=>`<tr>
    <td><b>${r.veiculo}</b></td><td>${r.tipo}</td><td>${r.sistema}</td><td>${r.responsavel}</td>
    <td>${r.entrada||'-'}</td><td>${r.saidaPrev||'-'}</td><td>${r.saidaReal||'-'}</td>
    <td>${badgePrio(r.prioridade)}</td><td>${badgeStatusM(r.status)}</td>
    <td>${diasParado(r)??'-'}</td><td>${r.custo?('R$ '+r.custo.toFixed(2)):'-'}</td>
    <td class="row-actions"><button onclick="editarM('${r.id}')">✏️</button><button onclick="excluirM('${r.id}')">🗑</button></td>
  </tr>`).join('');
}
function renderManutDash(){
  const kp=document.getElementById('manut-kpis');
  if(!manut.length){kp.innerHTML='';Object.values(mcharts).forEach(c=>c.destroy());mcharts={};return;}
  const abertos=manut.filter(r=>r.status!=='Concluído'&&r.status!=='Cancelado');
  const concl=manut.filter(r=>r.status==='Concluído');
  const lts=concl.map(r=>diasEntre(r.entrada,r.saidaReal)).filter(x=>x!=null);
  const ltm=lts.length?lts.reduce((a,b)=>a+b,0)/lts.length:0;
  const atrM=manut.length?manut.map(atrasoM).reduce((a,b)=>a+b,0)/manut.length:0;
  const ct=manut.reduce((s,r)=>s+(r.custo||0),0);
  const noPrazo=concl.filter(r=>!r.saidaPrev||(r.saidaReal&&r.saidaReal<=r.saidaPrev)).length;
  const ader=concl.length?(noPrazo/concl.length*100):0;

  kp.innerHTML=
    kpi('Em manutenção',abertos.length,'veículos parados','info')+
    kpi('Concluídas',concl.length,'OS finalizadas','ok')+
    kpi('Tempo médio',ltm.toFixed(1)+' d','lead time reparo','purple')+
    kpi('Atraso médio',atrM.toFixed(1)+' d','vs. previsto',atrM>3?'bad':'warn')+
    kpi('Custo total','R$ '+ct.toFixed(2),'soma de OS','info')+
    kpi('Aderência prazo',ader.toFixed(0)+'%',noPrazo+'/'+concl.length,ader>=80?'ok':ader>=50?'warn':'bad')+
    kpi('Críticas abertas',abertos.filter(r=>r.prioridade==='Crítica').length,'atenção','bad');

  Object.values(mcharts).forEach(c=>c.destroy());mcharts={};
  const cor=['#3b82f6','#22c55e','#f59e0b','#ef4444','#06b6d4','#a855f7','#94a3b8'];
  const opt={plugins:{legend:{labels:{color:'#e6ecff',font:{size:11}}}},scales:{x:{ticks:{color:'#8da0c7'},grid:{color:'#243056'}},y:{ticks:{color:'#8da0c7'},grid:{color:'#243056'}}}};
  const pie={plugins:{legend:{labels:{color:'#e6ecff',font:{size:11}}}}};
  const g=(k)=>manut.reduce((m,r)=>{m[r[k]]=(m[r[k]]||0)+1;return m;},{});
  const gs=g('status'),gt=g('tipo'),gsi=g('sistema'),gp=g('prioridade');
  mcharts.s=new Chart(document.getElementById('mch-status'),{type:'doughnut',data:{labels:Object.keys(gs),datasets:[{data:Object.values(gs),backgroundColor:cor}]},options:pie});
  mcharts.t=new Chart(document.getElementById('mch-tipo'),{type:'bar',data:{labels:Object.keys(gt),datasets:[{label:'OS',data:Object.values(gt),backgroundColor:'#3b82f6'}]},options:opt});
  mcharts.si=new Chart(document.getElementById('mch-sistema'),{type:'bar',data:{labels:Object.keys(gsi),datasets:[{label:'OS',data:Object.values(gsi),backgroundColor:'#a855f7'}]},options:opt});
  mcharts.p=new Chart(document.getElementById('mch-prio'),{type:'doughnut',data:{labels:Object.keys(gp),datasets:[{data:Object.values(gp),backgroundColor:['#94a3b8','#06b6d4','#f59e0b','#ef4444']}]},options:pie});
}

/* ============ HELPERS ============ */
function kpi(label,value,hint,cls){return `<div class="kpi ${cls||''}"><div class="label">${label}</div><div class="value">${value}</div><div class="hint">${hint||''}</div></div>`;}

/* ============ EXEMPLOS / IO ============ */
function carregarExemplos(){
  if((tarefas.length||manut.length)&&!confirm('Substituir dados existentes pelos exemplos?'))return;
  const hoje=new Date();const d=n=>{const x=new Date(hoje);x.setDate(x.getDate()+n);return x.toISOString().slice(0,10);};
  const veics=['GLB-0101','GLB-0102','GLB-0103','GLB-0104','GLB-0105','GLB-0106'];
  const resps=['João Silva','Maria Souza','Carlos Lima','Ana Pereira','Pedro Costa'];
  const tar=['Instalação chicote','Conferência fusíveis','Teste bateria','Montagem painel','Iluminação interna','Sensor ABS','Conector traseiro'];
  const sts=['Não iniciado','Em andamento','Concluído','Atrasado'];
  tarefas=[];
  for(let i=0;i<40;i++){
    const pi=d(-20+Math.floor(Math.random()*30));
    const pf=d(-20+Math.floor(Math.random()*30)+5);
    const st=sts[i%sts.length];
    tarefas.push({id:uid(),veiculo:veics[i%veics.length],fase:'Fase '+((i%3)+1),tarefa:tar[i%tar.length],
      responsavel:resps[i%resps.length],pi,pf,
      ri:st!=='Não iniciado'?pi:'',
      rf:st==='Concluído'?d(-20+Math.floor(Math.random()*30)+6):'',
      status:st,rubrica:Math.random()>.4?'Sim':'Não',obs:''});
  }
  const tipos=['Preventiva','Corretiva','Preditiva','Revisão','Inspeção'];
  const sist=['Elétrico','Mecânico','Hidráulico','Pneumático','Funilaria','Pintura'];
  const prios=['Baixa','Média','Alta','Crítica'];
  const stsM=['Aguardando','Em manutenção','Aguardando peça','Concluído','Em manutenção','Concluído'];
  manut=[];
  for(let i=0;i<20;i++){
    const ent=d(-Math.floor(Math.random()*35));
    const st=stsM[i%stsM.length];
    const sp=new Date(new Date(ent).getTime()+(5+Math.floor(Math.random()*10))*86400000).toISOString().slice(0,10);
    const sr=st==='Concluído'?new Date(new Date(sp).getTime()+(Math.floor(Math.random()*6)-2)*86400000).toISOString().slice(0,10):'';
    manut.push({id:uid(),veiculo:veics[i%veics.length],tipo:tipos[i%tipos.length],sistema:sist[i%sist.length],
      responsavel:resps[i%resps.length],entrada:ent,saidaPrev:sp,saidaReal:sr,
      prioridade:prios[i%prios.length],status:st,custo:Math.round(Math.random()*5000+200),obs:'Exemplo #'+(i+1)});
  }
  saveT();saveM();renderTarefas();renderDashboard();renderManut();renderManutDash();toast('Exemplos carregados ✓');
}
function exportarJSON(){
  const blob=new Blob([JSON.stringify({tarefas,manut},null,2)],{type:'application/json'});
  const a=document.createElement('a');a.href=URL.createObjectURL(blob);
  a.download='globe_dashboard_'+new Date().toISOString().slice(0,10)+'.json';a.click();
}
function importarJSON(e){
  const f=e.target.files[0];if(!f)return;
  const r=new FileReader();
  r.onload=ev=>{try{const obj=JSON.parse(ev.target.result);
    if(Array.isArray(obj)){tarefas=obj;}
    else{tarefas=obj.tarefas||[];manut=obj.manut||[];}
    saveT();saveM();renderTarefas();renderDashboard();renderManut();renderManutDash();toast('Importado ✓');
  }catch{toast('Arquivo inválido',true);}};
  r.readAsText(f);e.target.value='';
}
function limparTudo(){
  if(!confirm('Apagar TODAS as tarefas e manutenções?'))return;
  tarefas=[];manut=[];saveT();saveM();renderTarefas();renderDashboard();renderManut();renderManutDash();toast('Tudo limpo');
}

renderTarefas();
</script>
</body>
</html>
