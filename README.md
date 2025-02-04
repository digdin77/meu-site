<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simulação de Bot Financeiro</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f9f9f9;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    .container {
      max-width: 500px;
      width: 100%;
      background: white;
      border-radius: 8px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      overflow: hidden;
    }

    .header {
      background-color: #4CAF50;
      color: white;
      padding: 15px;
      text-align: center;
      font-size: 18px;
    }

    .chat-window {
      padding: 15px;
      height: 300px;
      overflow-y: auto;
      background: #f4f4f4;
      border-bottom: 1px solid #ddd;
    }

    .chat-window p {
      margin: 10px 0;
      padding: 10px;
      border-radius: 5px;
    }

    .bot-message {
      background: #e3e3e3;
      text-align: left;
    }

    .user-message {
      background: #4CAF50;
      color: white;
      text-align: right;
    }

    .input-area {
      display: flex;
      padding: 10px;
      background: #fff;
    }

    .input-area input {
      flex: 1;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 5px;
    }

    .input-area button {
      margin-left: 10px;
      padding: 10px 15px;
      background: #4CAF50;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    .input-area button:hover {
      background: #45a049;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">Como Funciona?</div>
    <div class="chat-window" id="chat-window">
      <p class="bot-message">Olá! Eu sou seu assistente financeiro. Digite um gasto para começar, exemplo: "camisa 110".</p>
    </div>
    <div class="input-area">
      <input type="text" id="user-input" placeholder="Exemplo: ifood 44">
      <button onclick="sendMessage()">Enviar</button>
    </div>
  </div>

  <script>
    const chatWindow = document.getElementById('chat-window');
    const userInput = document.getElementById('user-input');

    function sendMessage() {
      const message = userInput.value.trim();

      if (message) {
        // Exibir mensagem do usuário
        const userMessage = document.createElement('p');
        userMessage.className = 'user-message';
        userMessage.innerText = message;
        chatWindow.appendChild(userMessage);

        // Responder automaticamente
        const botMessage = document.createElement('p');
        botMessage.className = 'bot-message';

        if (message.toLowerCase().includes('camisa') || message.toLowerCase().includes('ifood')) {
          botMessage.innerText = `Gasto adicionado: ${message}. ✅`;
        } else {
          botMessage.innerText = 'Desculpe, não entendi. Por favor, insira um gasto válido, como "camisa 110".';
        }

        chatWindow.appendChild(botMessage);

        // Limpar campo de entrada
        userInput.value = '';

        // Rolar para a última mensagem
        chatWindow.scrollTop = chatWindow.scrollHeight;
      }
    }
  </script>
</body>
</html>
