<!DOCTYPE html><html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Anúncios Ruy Barbosa</title>
  <style>
    body { font-family: Arial; margin: 0; background: #f4f4f4; }
    header { background: #2c3e50; color: white; padding: 15px; text-align: center; }
    .container { padding: 20px; }
    .card { background: white; padding: 15px; margin-bottom: 10px; border-radius: 8px; }
    input, textarea, button {
      width: 100%; margin-top: 10px; padding: 10px;
    }
    button { background: #27ae60; color: white; border: none; cursor: pointer; }
  </style>
</head>
<body><header>
  <h1>Venda Fácil - Ruy Barbosa BA</h1>
  <p>Publique seu produto por apenas R$0,99</p>
</header><div class="container">  <h2>Postar Produto</h2>
  <input type="text" id="titulo" placeholder="Nome do produto">
  <textarea id="descricao" placeholder="Descrição"></textarea>
  <input type="number" id="preco" placeholder="Preço">
  <button onclick="postar()">Publicar (R$0,99)</button>  <h2>Anúncios</h2>
  <div id="lista"></div></div><script>
  let anuncios = [];

  function postar() {
    let titulo = document.getElementById('titulo').value;
    let descricao = document.getElementById('descricao').value;
    let preco = document.getElementById('preco').value;

    if (!titulo || !descricao || !preco) {
      alert('Preencha tudo!');
      return;
    }

    let anuncio = { titulo, descricao, preco };
    anuncios.push(anuncio);
    render();
  }

  function render() {
    let lista = document.getElementById('lista');
    lista.innerHTML = '';

    anuncios.forEach(a => {
      lista.innerHTML += `
        <div class="card">
          <h3>${a.titulo}</h3>
          <p>${a.descricao}</p>
          <strong>R$ ${a.preco}</strong>
        </div>
      `;
    });
  }
</script></body>
</html>