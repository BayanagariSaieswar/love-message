<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>I Love You Kannu</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(to right, #ff0066, #ff3399);
      overflow: hidden;
      font-family: 'Segoe UI', sans-serif;
      animation: fadeIn 3s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      height: 100vh;
      color: white;
    }

    h1 {
      font-size: 4.5em;
      font-weight: bold;
      margin: 0;
      animation: glow 2s infinite alternate;
      text-shadow: 3px 3px 10px rgba(0,0,0,0.3);
    }

    @keyframes glow {
      from {
        text-shadow: 0 0 10px #fff, 0 0 20px #ff3399, 0 0 30px #ff3399;
      }
      to {
        text-shadow: 0 0 20px #fff, 0 0 30px #ff99cc, 0 0 40px #ff66cc;
      }
    }

    .heart {
      position: absolute;
      width: 25px;
      height: 25px;
      background: url('https://cdn-icons-png.flaticon.com/512/833/833472.png') no-repeat center;
      background-size: contain;
      animation: float 10s linear infinite;
      opacity: 0.7;
    }

    @keyframes float {
      0% {
        transform: translateY(100vh) rotate(0deg);
        opacity: 0.3;
      }
      100% {
        transform: translateY(-100vh) rotate(360deg);
        opacity: 0.9;
      }
    }

    audio {
      display: none;
    }

    .button-container {
      margin-top: 30px;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    button {
      padding: 12px 25px;
      font-size: 16px;
      border: none;
      border-radius: 25px;
      background-color: white;
      color: #ff3399;
      cursor: pointer;
      font-weight: bold;
      box-shadow: 0px 5px 15px rgba(255, 0, 102, 0.3);
      transition: all 0.3s ease;
    }

    button:hover {
      background-color: #ff99cc;
      color: white;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>I Love You Kannu 💖</h1>
    <div class="button-container">
      <button onclick="playMusic()">🎵 Play Background Music</button>
      <button onclick="playVoice()">💌 Tap to Hear Voice Note</button>
      <button onclick="restartPage()">💞 Restart Love</button>
    </div>
  </div>

  <!-- Background Love Music -->
  <audio id="loveMusic" autoplay loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
    Your browser does not support the audio tag.
  </audio>

  <!-- Voice Note -->
  <audio id="voiceNote">
    <source src="https://www2.cs.uic.edu/~i101/SoundFiles/StarWars60.wav" type="audio/wav">
    <!-- Replace above link with your real voice note MP3/WAV -->
  </audio>

  <!-- Floating Hearts -->
  <script>
    for (let i = 0; i < 35; i++) {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.style.left = `${Math.random() * 100}vw`;
      heart.style.animationDuration = `${4 + Math.random() * 6}s`;
      document.body.appendChild(heart);
    }

    function playMusic() {
      document.getElementById("loveMusic").play();
    }

    function playVoice() {
      document.getElementById("voiceNote").play();
    }

    function restartPage() {
      location.reload();
    }
  </script>

</body>
</html>
