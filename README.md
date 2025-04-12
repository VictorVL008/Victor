<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>VJjogos</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 20px;
    }
    h1 {
      color: #333;
      text-align: center;
    }
    .form {
      max-width: 500px;
      margin: 20px auto;
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    input {
      width: calc(100% - 22px);
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    button {
      background-color: #4CAF50;
      color: white;
      padding: 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    ul {
      list-style: none;
      padding: 0;
    }
    li a {
      text-decoration: none;
      color: #007BFF;
    }
    .jogo {
      background: white;
      margin: 10px auto;
      padding: 10px;
      border-radius: 5px;
      max-width: 500px;
      box-shadow: 0 0 5px rgba(0,0,0,0.1);
    }
  </style>
</head>
<body>
  <h1>VJjogos</h1>
  <div class="form">
    <input type="text" id="nomeJogo" placeholder="Nome do jogo" />
    <input type="text" id="linkJogo" placeholder="Link do jogo (https://...)" />
    <button onclick="adicionarJogo()">Adicionar Jogo</button>
  </div>
  <ul id="listaDeJogos"></ul>  <script>
    const listaDeJogos = JSON.parse(localStorage.getItem("jogos")) || [];

    function renderizarJogos() {
      const ul = document.getElementById("listaDeJogos");
      ul.innerHTML = "";
      listaDeJogos.forEach(jogo => {
        const li = document.createElement("li");
        li.classList.add("jogo");
        li.innerHTML = `<strong>${jogo.nome}</strong><br><a href="${jogo.link}" target="_blank">Jogar</a>`;
        ul.appendChild(li);
      });
    }

    function adicionarJogo() {
      const nome = document.getElementById("nomeJogo").value;
      const link = document.getElementById("linkJogo").value;
      if (!nome || !link) return alert("Preencha todos os campos!");

      listaDeJogos.push({ nome, link });
      localStorage.setItem("jogos", JSON.stringify(listaDeJogos));
      renderizarJogos();

      document.getElementById("nomeJogo").value = "";
      document.getElementById("linkJogo").value = "";
    }

    renderizarJogos();
  </script></body>
</html>
