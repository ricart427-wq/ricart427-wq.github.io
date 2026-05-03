<!doctype html>
<html lang="pt-BR" class="h-full">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Geladinhos da mily 🍦</title>

<script src="https://cdn.tailwindcss.com"></script>
<script src="https://cdn.jsdelivr.net/npm/lucide@latest"></script>

<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">

<style>
body { margin:0; font-family:'Nunito',sans-serif; background:#fffbf0; }
.card-pop:hover { transform: translateY(-4px); }
</style>
</head>

<body>

<h1 style="text-align:center;color:#e11d48;">Geladinhos da mily🍦</h1>

<div id="products"></div>

<script>
const PRODUCTS = [
  { id:1, name:'Morango', price:4 },
  { id:2, name:'Maracujá', price:3.5 },
  { id:3, name:'Chocolate', price:5 }
];

let cart = {};

function render(){
  const div = document.getElementById('products');
  div.innerHTML = PRODUCTS.map(p=>`
    <div style="border:1px solid #ccc;padding:10px;margin:10px;">
      <h3>${p.name}</h3>
      <p>R$ ${p.price}</p>
      <button onclick="add(${p.id})">Adicionar</button>
    </div>
  `).join('');
}

function add(id){
  cart[id]=(cart[id]||0)+1;
  alert('Adicionado!');
}

render();

// evita erro se lucide não carregar
if(window.lucide){
  lucide.createIcons();
}
</script>

</body>
</html>
