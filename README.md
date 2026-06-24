
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>ERP Motorhomes • Globe</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<style>

body{
margin:0;
font-family:Arial;
background:#0a0f1c;
color:#fff;
}

/* LAYOUT ERP */
.header{
background:#0f172a;
padding:15px;
font-size:18px;
display:flex;
justify-content:space-between;
}

.grid{
display:grid;
grid-template-columns:1fr 2fr;
gap:10px;
padding:10px;
}

/* SIDEBAR */
.sidebar{
background:#111a2e;
padding:10px;
height:90vh;
overflow:auto;
}

/* DASHBOARD */
.card{
background:#121c33;
padding:10px;
margin-bottom:10px;
border-radius:8px;
}

/* ALERTA */
.alert{
animation:blink 0.8s infinite;
background:#3a0d0d;
border-left:4px solid red;
padding:8px;
}

@keyframes blink{
50%{opacity:0.4;}
}

/* BUTTONS */
button{
background:#2563eb;
color:#fff;
border:none;
padding:8px;
margin:3px;
border-radius:6px;
cursor:pointer;
}

button:hover{background:#1d4ed8;}

input, select{
width:100%;
padding:6px;
margin:5px 0;
}

/* VEHICLE CARD */
.vehicle{
background:#0f172a;
padding:8px;
margin:6px 0;
border-radius:6px;
cursor:pointer;
}

.vehicle:hover{
background:#1e293b;
}

</style>
</head>

<body>

<div class="header">
<div>ERP MOTORHOMES • GLOBE SYSTEM</div>
<div id="hora"></div>
</div>

<div class="grid">

<!-- SIDEBAR -->
<div class="sidebar">

<h3>Veículos</h3>
<div id="listaVeiculos"></div>

<hr>

<h3>Nova OS</h3>

<input id="cliente" placeholder="Cliente">
<input id="veiculo" placeholder="Veículo">
<input id="data" type="date">
<input id="horas" type="number" placeholder="Horas">

<select id="status">
<option>em andamento</option>
<option>executado</option>
<option>aguardando peças</option>
<option>parado</option>
<option>concluido</option>
</select>

<button onclick="addOS()">Salvar</button>

</div>

<!-- DASHBOARD -->
<div>

<div class="card">
<h3>Indicadores ERP</h3>

<div id="kpi"></div>
</div>

<div class="card">
<canvas id="chart"></canvas>
</div>

<div class="card">
<h3>Histórico do Veículo</h3>
<div id="historico"></div>

<button onclick="gerarPDF()">📄 Gerar PDF</button>
<button onclick="enviarWhats()">📲 WhatsApp</button>

</div>

</div>

</div>

<script>

let os = JSON.parse(localStorage.getItem("os")) || [];
let veiculoSelecionado = null;

/* CLOCK */
setInterval(()=>{
document.getElementById("hora").innerText=new Date().toLocaleString();
},1000);

/* ADD OS */
function addOS(){

os.push({
cliente:cliente.value,
veiculo:veiculo.value,
data:data.value,
horas:horas.value,
status:status.value
});

localStorage.setItem("os",JSON.stringify(os));
render();
}

/* LISTA VEICULOS */
function renderVeiculos(){

let lista = document.getElementById("listaVeiculos");
lista.innerHTML="";

let veiculos = [...new Set(os.map(o=>o.veiculo))];

veiculos.forEach(v=>{

let div=document.createElement("div");
div.className="vehicle";

div.innerHTML=v;

div.onclick=()=> {
veiculoSelecionado=v;
renderHistorico();
};

lista.appendChild(div);

});

}

/* HISTORICO */
function renderHistorico(){

let h=document.getElementById("historico");
h.innerHTML="";

let filtro=os.filter(o=>o.veiculo===veiculoSelecionado);

filtro.forEach(o=>{

h.innerHTML+=`
<div class="card">
<b>${o.cliente}</b><br>
Status: ${o.status}<br>
Horas: ${o.horas}<br>
Data: ${o.data}
</div>
`;

});

}

/* KPI */
function renderKPI(){

document.getElementById("kpi").innerHTML=`
Total OS: ${os.length}<br>
Em andamento: ${os.filter(o=>o.status==="em andamento").length}<br>
Executado: ${os.filter(o=>o.status==="executado").length}<br>
Parado: ${os.filter(o=>o.status==="parado").length}
`;

}

/* CHART */
function chart(){

new Chart(document.getElementById("chart"),{
type:"pie",
data:{
labels:["Andamento","Executado","Parado"],
datasets:[{
data:[
os.filter(o=>o.status==="em andamento").length,
os.filter(o=>o.status==="executado").length,
os.filter(o=>o.status==="parado").length
]
}]
}
});

}

/* PDF REAL */
function gerarPDF(){

const { jsPDF } = window.jspdf;
const doc = new jsPDF();

doc.text("RELATÓRIO MOTORHOMES",10,10);

let y=20;

os.forEach(o=>{
doc.text(`${o.veiculo} | ${o.status} | ${o.horas}h`,10,y);
y+=10;
});

doc.save("relatorio.pdf");

}

/* WHATSAPP */
function enviarWhats(){

let texto = "RELATÓRIO MOTORHOMES\n\n";

os.forEach(o=>{
texto += `${o.veiculo} - ${o.status} - ${o.horas}h\n`;
});

let url = `https://wa.me/?text=${encodeURIComponent(texto)}`;

window.open(url,"_blank");

}

/* INIT */
function render(){
renderVeiculos();
renderKPI();
chart();
}

render();

</script>

</body>
</html>
