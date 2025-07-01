<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Gender Reveal Surprise!</title>
  <style>
    body {
      font-family: "Helvetica Neue", sans-serif;
      background: linear-gradient(135deg, #e3f2fd, #f0f4c3);
      text-align: center;
      padding: 40px 20px;
    }
    h1 {
      color: #333;
      font-size: 2em;
    }
    .message {
      font-size: 1.2em;
      margin-top: 10px;
      color: #555;
    }
    .button {
      margin-top: 40px;
      padding: 15px 30px;
      font-size: 1.2em;
      background-color: #2196f3;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    .button:hover {
      background-color: #1976d2;
    }
    .countdown {
      font-size: 2em;
      margin-top: 30px;
      color: #007acc;
      display: none;
    }
    .result {
      font-size: 2.2em;
      font-weight: bold;
      color: #2196f3;
      display: none;
      margin-top: 40px;
    }
  </style>
</head>
<body>

  <h1>🎈 サプライズ発表 🎈</h1>
  <p class="message">ボタンを押してね！</p>

  <button class="button" id="startBtn">タップしてスタート！</button>

  <div class="countdown" id="countdown">5</div>

  <div class="result" id="resultText">💙 It's a Boy! 💙</div>

  <script>
    const startBtn = document.getElementById("startBtn");
    const countdownEl = document.getElementById("countdown");
    const resultText = document.getElementById("resultText");

    startBtn.addEventListener("click", () => {
      startBtn.style.display = "none";
      countdownEl.style.display = "block";

      let timeLeft = 5;
      countdownEl.textContent = timeLeft;

      const timer = setInterval(() => {
        timeLeft--;
        countdownEl.textContent = timeLeft;

        if (timeLeft <= 0) {
          clearInterval(timer);
          countdownEl.style.display = "none";
          resultText.style.display = "block";
        }
      }, 1000);
    });
  </script>

</body>
</html>
