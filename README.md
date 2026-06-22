<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Sistema Elétrico - Login</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
body{margin:0;font-family:Arial;background:#0b1220;color:#fff}

/* LOGIN */
#loginPage{
display:flex;justify-content:center;align-items:center;height:100vh;
}
.loginBox{
background:#121a2e;padding:30px;border-radius:12px;width:300px
}
input{
width:100%;padding:10px;margin:10px 0;border:0;border-radius:6px
}
button{
width:100%;padding:10px;background:#3b82f6;border:0;color:#fff;border-radius:6px;cursor:pointer
}

/* DASHBOARD */
#app{display:none}
header{
display:flex;justify-content:space-between;padding:15px;background:#111a33
}
.logout{
background:#ef4444;padding:8px 12px;border:0;color:#fff;border-radius:6px;cursor:pointer
}

.container{padding:20px}
.card{background:#121a2e;padding:15px;border-radius:10px;margin-bottom:15px}
</style>
</head>

<body>

<!-- LOGIN -->
<div id="loginPage">
  <div class="loginBox">
    <h2>Login Sistema</h2>
    <input id="user" placeholder="Usuário">
    <input id="pass" type="password" placeholder="Senha">
    <button onclick="login()">Entrar</button>
  </div>
</div>

<!-- APP -->
<div id="app">

<header>
  <div>⚡ Sistema Elétrico</div>
  <button class="logout" onclick="logout()">Sair</button>
</header>

<div class="container">

  <div class="card">
    <h3>Dashboard básico</h3>
    <p>Bem-vindo ao sistema local da empresa.</p>
  </div>

  <div class="card">
    <h3>Adicionar tarefa (teste)</h3>
    <input id="tarefa" placeholder="Nome tarefa">
    <button onclick="addTask()">Salvar</button>
  </div>

  <div class="card">
    <h3>Tarefas</h3>
    <div id="lista"></div>
  </div>

</div>

</div>

<script>

// 🔐 LOGIN SIMPLES
function login(){
  const u = document.getElementById('user').value;
  const p = document.getElementById('pass').value;

  if(u === "admin" && p === "1234"){
    localStorage.setItem("logado", "1");
    showApp();
  }else{
    alert("Login inválido");
  }
}

function logout(){
  localStorage.removeItem("logado");
  location.reload();
}

function showApp(){
  document.getElementById("loginPage").style.display="none";
  document.getElementById("app").style.display="block";
}

// verificar login
if(localStorage.getItem("logado") === "1"){
  showApp();
}

// 📦 tarefas simples local
let tarefas = JSON.parse(localStorage.getItem("tarefas")||"[]");

function addTask(){
  const t = document.getElementById("tarefa").value;
  if(!t)return;

  tarefas.push(t);
  localStorage.setItem("tarefas", JSON.stringify(tarefas));
  render();
}

function render(){
  document.getElementById("lista").innerHTML =
    tarefas.map(t=>`• ${t}`).join("<br>");
}

render();

</script>

</body>
</html>
