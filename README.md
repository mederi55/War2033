<!DOCTYPE html><html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>IventWar 2033 - Статус Сервера</title>
  <style>
    body {
      background: radial-gradient(circle, #1a1a1a, #000);
      color: #f0f0f0;
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      padding: 20px;
      text-align: center;
    }
    h1 {
      font-size: 2.5em;
      color: #e63946;
    }
    p {
      font-size: 1.2em;
      max-width: 600px;
    }
    #status {
      margin-top: 20px;
      font-size: 1.5em;
      padding: 10px 20px;
      border-radius: 10px;
    }
    .online {
      background-color: #2a9d8f;
    }
    .offline {
      background-color: #e76f51;
    }
  </style>
</head>
<body>
  <h1>IventWar 2033</h1>
  <p>
    Мир охвачен пламенем. Год — 2033.<br />
    Человечество на грани исчезновения.<br />
    Разрушенные города, опустевшие земли, и лишь горстка героев решает судьбу планеты.<br /><br />
    <strong>Сможешь ли ты спасти этот мир... или обрушишь его в пепел?</strong>
  </p>  <div id="status" class="offline">Проверка статуса сервера...</div>  <script>
    async function checkServerStatus() {
      try {
        const response = await fetch("https://api.mcstatus.io/v2/status/java/Iventwar2033.aternos.me:56896");
        const data = await response.json();
        const statusDiv = document.getElementById("status");

        if (data.online) {
          statusDiv.textContent = "Сервер онлайн — игроков: " + data.players.online;
          statusDiv.className = "online";
        } else {
          statusDiv.textContent = "Сервер оффлайн";
          statusDiv.className = "offline";
        }
      } catch (error) {
        document.getElementById("status").textContent = "Ошибка проверки статуса.";
      }
    }

    checkServerStatus();
    setInterval(checkServerStatus, 30000); // проверять каждые 30 сек
  </script></body>
</html>
