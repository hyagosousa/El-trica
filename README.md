<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Dashboard Fase Elétrica - Globe</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-adapter-date-fns/dist/chartjs-adapter-date-fns.bundle.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/jspdf@2.5.1/dist/jspdf.umd.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/jspdf-autotable@3.8.2/dist/jspdf.plugin.autotable.min.js"></script>

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
.btn.wa{background:#25d366;color:#0b1220}

.tabs{display:flex;gap:6px;padding:0 28px;background:var(--panel);border-bottom:1px solid var(--border);flex-wrap:wrap}
.tab{padding:14px 18px;cursor:pointer;color:var(--muted);font-weight:600;border-bottom:3px solid transparent;font-size:13px}
.tab.active{color:var(--text);border-color:var(--accent)}

.container{padding:20px 28px;max-width:1600px;margin:0 auto}
.view{display:none}.view.active{display:block}

.card{background:var(--panel);border:1px solid var(--border);border-radius:12px;padding:16px;margin-bottom:16px}
h3{margin:0 0 12px 0;font-size:14px;font-weight:600}

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

@media(max-width:1100px){
.container{padding:12px}
}
</style>
</head>

<body>

<header>
<div>
<h1>⚡ Dashboard Fase Elétrica - Globe</h1>
<div class="sub">Sistema industrial completo</div>
</div>
</header>

<div class="tabs">
<div class="tab active">📝 Entrada</div>
<div class="tab">📊 Dashboard</div>
<div class="tab">🔧 Manutenções</div>
</div>

<div class="container">

<div class="card">
<h3>👷 Horas por eletricista × carro</h3>
<div id="listaHoras"></div>
</div>

<div class="card">
<h3>🔧 Manutenções</h3>
<div class="scroll">
<table>
<thead>
<tr>
<th>Carro</th>
<th>Profissional</th>
<th>Horas</th>
</tr>
</thead>
<tbody id="tabela"></tbody>
</table>
</div>
</div>

</div>

<script>

let db = {
manutencoes:[
{carro:"GLB-001",prof:"Carlos",horas:4},
{carro:"GLB-001",prof:"Carlos",horas:4.5},
{carro:"GLB-002",prof:"João",horas:3},
{carro:"GLB-003",prof:"Ana",horas:5}
]
};

function render(){

let map = {};

db.manutencoes.forEach(m=>{
if(!map[m.prof]) map[m.prof]={total:0,cars:{}};

map[m.prof].total += m.horas;

if(!map[m.prof].cars[m.carro]) map[m.prof].cars[m.carro]=0;

map[m.prof].cars[m.carro]+=m.horas;
});

let html = "";

Object.keys(map).forEach(p=>{
let cars = Object.entries(map[p].cars)
.map(c=>`🚗 ${c[0]} - ${c[1].toFixed(2)}h`)
.join(" · ");

html += `<div><b>👷 ${p}</b> - ${map[p].total.toFixed(2)}h<br><small>${cars}</small></div><br>`;
});

document.getElementById("listaHoras").innerHTML = html;

let tb = "";

db.manutencoes.forEach(m=>{
tb += `<tr>
<td>${m.carro}</td>
<td>${m.prof}</td>
<td>${m.horas}</td>
</tr>`;
});

document.getElementById("tabela").innerHTML = tb;

}

render();

</script>

</body>
</html>
