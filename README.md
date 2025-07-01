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
    .countdown {
      font-size: 2em;
      margin-top: 30px;
      color: #007acc;
    }
    .reveal-box {
      margin-top: 40px;
      background-color: #fff;
      border-radius: 12px;
      padding: 30px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      cursor: pointer;
      transition: transform 0.2s;
      display: none;
    }
    .reveal-box:hover {
      transform: scale(1.02);
    }
    .result {
      font-size: 2em;
      font-weight: bold;
      color: #2196f3;
      display: none;
      margin-top: 20px;
    }
    .balloon {
      font-size: 3em;
      animation: float 2s ease-in-out infinite;
    }
    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }
    audio {
      display: none;
    }
  </style>
</head>
<body>

  <h1>🎈 サプライズ発表 🎈</h1>
  <p class="message">私たちの赤ちゃんの性別、カウントダウンの後に発表します！</p>

  <div class="countdown" id="countdown">00:00</div>

  <div class="reveal-box" id="revealBox" onclick="revealGender()">
    <div class="balloon">🎈🎈🎈</div>
    <p>タップして発表を見る！</p>
    <div class="result" id="resultText">💙 It's a Boy! 💙</div>
  </div>

  <audio id="bgMusic" loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mp3">
    Your browser does not support the audio element.
  </audio>

  <script>
    // カウントダウン設定（例：10秒後）
    let seconds = 10;
    const countdownEl = document.getElementById("countdown");
    const revealBox = document.getElementById("revealBox");
    const music = document.getElementById("bgMusic");

    const timer = setInterval(() => {
      countdownEl.textContent = `00:${seconds.toString().padStart(2, '0')}`;
      seconds--;
      if (seconds < 0) {
        clearInterval(timer);
        countdownEl.style.display = "none";
        revealBox.style.display = "block";
        // 音楽再生（ユーザー操作後でなければ再生されない可能性あり）
        music.play().catch(() => {
          console.log("音楽はユーザー操作後に再生されます");
        });
      }
    }, 1000);

    function revealGender() {
      document.getElementById("resultText").style.display = "block";
    }
  </script>

</body>
</html>
