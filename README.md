<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Login e Estoque</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 2rem;
      background: #f4f4f4;
    }
    h1, h2 {
      color: #333;
    }
    form, table, .login {
      background: #fff;
      padding: 1rem;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      margin-bottom: 2rem;
    }
    input, button {
      padding: 0.5rem;
      margin-right: 1rem;
      margin-bottom: 1rem;
    }
    table {
      width: 100%;
      border-collapse: collapse;
    }
    th, td {
      border: 1px solid #ccc;
      padding: 0.5rem;
      text-align: left;
    }
    th {
      background: #eee;
    }
    #estoqueSection {
      display: none;
    }
  </style>
</head>
<body>
  <h1>Sistema de Estoque</h1>

  <div class="login" id="loginSection">
    <h2>Login do Administrador</h2>
    <input type="text" id="usuario" placeholder="Usuário" required>
    <input type="password" id="senha" placeholder="Senha" required>
    <button onclick="fazerLogin()">Entrar</button>
    <p id="mensagemErro" style="color:red;"></p>
  </div>

  <div id="estoqueSection">
    <form id="formProduto">
      <input type="text" id="nome" placeholder="Nome do Produto" required>
      <input type="number" id="quantidade" placeholder="Quantidade" required>
      <button type="submit">Adicionar Produto</button>
    </form>

    <table>
      <thead>
        <tr>
          <th>Produto</th>
          <th>Quantidade</th>
        </tr>
      </thead>
      <tbody id="listaProdutos"></tbody>
    </table>
  </div>

  <script>
    const usuarioCorreto = "1562";
    const senhaCorreta = "Leonardo80@";

    function fazerLogin() {
      const usuario = document.getElementById('usuario').value;
      const senha = document.getElementById('senha').value;
      const erro = document.getElementById('mensagemErro');

      if (usuario === usuarioCorreto && senha === senhaCorreta) {
        document.getElementById('loginSection').style.display = 'none';
        document.getElementById('estoqueSection').style.display = 'block';
      } else {
        erro.textContent = "Usuário ou senha incorretos.";
      }
    }

    const form = document.getElementById('formProduto');
    const lista = document.getElementById('listaProdutos');

    form.addEventListener('submit', function(event) {
      event.preventDefault();

      const nome = document.getElementById('nome').value.trim();
      const quantidade = parseInt(document.getElementById('quantidade').value);

      if (nome && quantidade >= 0) {
        const row = document.createElement('tr');
        row.innerHTML = `<td>${nome}</td><td>${quantidade}</td>`;
        lista.appendChild(row);

        form.reset();
      }
    });
  </script>
</body>
</html>
