<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Geladinhos da Mily 🍦</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>

<body class="bg-gray-100 text-gray-800">

<header class="bg-white shadow p-4 text-center">
  <h1 class="text-3xl font-bold">Geladinhos da Mily 🍦</h1>
  <p class="text-gray-500">Todos por R$2 • Entrega em 30 minutos 🚚</p>
  <p class="text-sm text-red-500">Entrega apenas sábado e domingo</p>
</header>

<main class="p-6 max-w-md mx-auto">

  <!-- SABORES -->
  <h2 class="text-xl font-bold mb-4 text-center">Escolha seus sabores</h2>

  <div id="produtos" class="space-y-3"></div>

  <!-- TOTAL -->
  <div class="bg-white p-4 rounded shadow mt-4">
    <p>Total de itens: <span id="qtd">0</span></p>
    <p>Total: R$ <span id="total">0</span></p>
    <p id="frete" class="text-sm text-gray-500"></p>
  </div>

  <!-- DADOS -->
  <div class="bg-white p-4 rounded shadow mt-4">
    <input id="nome" placeholder="Seu nome" class="w-full p-2 border mb-2 rounded">
    <input id="endereco" placeholder="Endereço completo" class="w-full p-2 border mb-2 rounded">
    <input id="ref" placeholder="Ponto de referência" class="w-full p-2 border rounded">
  </div>

  <!-- BOTÃO -->
  <button onclick="enviarPedido()" 
    class="w-full bg-green-500 text-white p-3 rounded mt-4 text-lg">
    Finalizar Pedido no WhatsApp
  </button>

</main>

<script>
let produtos = [
  {nome:"Coco 🥥", qtd:0, likes:0},
  {nome:"Manga 🥭", qtd:0, likes:0},
  {nome:"Maracujá 🍈", qtd:0, likes:0}
];

function render(){
  let html = "";
  produtos.forEach((p,i)=>{
    html += `
    <div class="bg-white p-4 rounded shadow">
      <div class="flex justify-between">
        <span>${p.nome} - R$2</span>
        <button onclick="like(${i})">❤️ ${p.likes}</button>
      </div>

      <div class="flex items-center mt-2 gap-2">
        <button onclick="menos(${i})">-</button>
        <span>${p.qtd}</span>
        <button onclick="mais(${i})">+</button>
      </div>
    </div>`;
  });
  document.getElementById("produtos").innerHTML = html;

  calcular();
}

function mais(i){ produtos[i].qtd++; render(); }
function menos(i){ if(produtos[i].qtd>0) produtos[i].qtd--; render(); }
function like(i){ produtos[i].likes++; render(); }

function calcular(){
  let totalQtd = produtos.reduce((s,p)=>s+p.qtd,0);
  let total = totalQtd * 2;
  let frete = 0;

  if(totalQtd < 3){
    document.getElementById("frete").innerText = "Pedido mínimo: 3 unidades";
  } else {
    if(totalQtd >= 5){
      document.getElementById("frete").innerText = "Frete grátis 🎉";
    } else {
      frete = 3;
      document.getElementById("frete").innerText = "Taxa de entrega: R$3";
    }
  }

  document.getElementById("qtd").innerText = totalQtd;
  document.getElementById("total").innerText = total + frete;
}

function enviarPedido(){
  let nome = document.getElementById("nome").value;
  let endereco = document.getElementById("endereco").value;
  let ref = document.getElementById("ref").value;

  let totalQtd = produtos.reduce((s,p)=>s+p.qtd,0);

  if(totalQtd < 3){
    alert("Pedido mínimo de 3 unidades!");
    return;
  }

  let mensagem = `Pedido - Geladinhos da Mily 🍦\n\n`;
  mensagem += `Nome: ${nome}\nEndereço: ${endereco}\nReferência: ${ref}\n\n`;

  produtos.forEach(p=>{
    if(p.qtd>0){
      mensagem += `${p.nome}: ${p.qtd}\n`;
    }
  });

  let total = totalQtd * 2;
  if(totalQtd < 5) total += 3;

  mensagem += `\nTotal: R$${total}`;

  let numero = "5575999806162";
  let url = "https://wa.me/" + numero + "?text=" + encodeURIComponent(mensagem);

  window.open(url, "_blank");
}

render();
</script>

</body>
</html>
