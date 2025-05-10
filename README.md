<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Love Surprise</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to right, #fff0f5, #ffe6f0);
      text-align: center;
      padding: 20px;
      overflow-x: hidden;
    }

    .hidden { display: none; }

    input {
      padding: 10px;
      margin: 10px;
      font-size: 16px;
      border: 2px solid #ff66b2;
      border-radius: 10px;
    }

    button {
      padding: 10px 20px;
      margin: 10px;
      background: #ff4da6;
      color: white;
      font-size: 16px;
      border: none;
      border-radius: 20px;
      cursor: pointer;
    }

    #roseBtn {
      font-size: 40px;
      background: transparent;
      border: none;
      animation: pulse 1s infinite;
      margin-top: 30px;
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.2); }
      100% { transform: scale(1); }
    }

    #letter {
      font-size: 100px;
      cursor: pointer;
      margin: 30px 0;
    }

    .love-card {
      background: red;
      color: white;
      font-size: 20px;
      padding: 20px;
      border-radius: 20px;
      max-width: 400px;
      margin: 20px auto;
    }

    .scene {
      display: flex;
      justify-content: space-around;
      align-items: center;
      font-size: 40px;
      margin-top: 40px;
      transition: all 0.8s ease;
    }

    .boy, .girl {
      transition: transform 1s;
    }

    .exchange {
      font-size: 30px;
      opacity: 0;
      transition: opacity 1s ease;
    }
  </style>
</head>
<body>

  <!-- Step 1: Ask Name -->
  <div id="step1">
    <h2>Hi dear! What's your name? 💖</h2>
    <input type="text" id="nameInput" placeholder="Enter your name" />
    <br />
    <button onclick="askDOB()">Next</button>
  </div>

  <!-- Step 2: Ask DOB -->
  <div id="step2" class="hidden">
    <h2>When is your birthday, <span id="displayName"></span>? 🎂</h2>
    <input type="date" id="dobInput" />
    <br />
    <button onclick="showCountdown()">Show Time Left</button>
  </div>

  <!-- Step 3: Show Countdown -->
  <div id="step3" class="hidden">
    <h2 id="countdownText"></h2>
    <button id="roseBtn" onclick="showLetter()">🌹</button>
    <p>Click the rose! I have some interesting news to update with you.</p>
  </div>

  <!-- Step 4: Show Letter -->
  <div id="letterSection" class="hidden">
    <div id="letter" onclick="showLoveCard()">💌</div>
    <p>Click the letter to open my heart!</p>
  </div>

  <!-- Step 5: Love Message Card -->
  <div id="loveCard" class="hidden">
    <div class="love-card">
      I love you so much, Kannu. My eyes are waiting for you...<br><br>
      ❤️ Love you, Kannu ❤️
    </div>
    <button onclick="startExchange()">Click to feel the magic 💞</button>
  </div>

  <!-- Final Scene: Boy meets Girl -->
  <div id="finalScene" class="hidden">
    <div class="scene">
      <div class="boy" id="boy">👦</div>
      <div class="girl" id="girl">👧</div>
    </div>
    <div class="exchange" id="exchange">💞 Love is exchanged 💞</div>
  </div>

  <script>
    let userName = "";

    function askDOB() {
      userName = document.getElementById("nameInput").value;
      if (!userName) {
        alert("Please enter your name!");
        return;
      }
      document.getElementById("step1").classList.add("hidden");
      document.getElementById("displayName").innerText = userName;
      document.getElementById("step2").classList.remove("hidden");
    }

    function showCountdown() {
      const dob = new Date(document.getElementById("dobInput").value);
      if (!dob || isNaN(dob)) {
        alert("Please enter a valid date!");
        return;
      }

      const now = new Date();
      const nextBirthday = new Date(now.getFullYear(), dob.getMonth(), dob.getDate());
      if (now > nextBirthday) {
        nextBirthday.setFullYear(now.getFullYear() + 1);
      }

      const diff = nextBirthday - now;
      const days = Math.floor(diff / (1000 * 60 * 60 * 24));
      const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const minutes = Math.floor((diff / (1000 * 60)) % 60);

      document.getElementById("step2").classList.add("hidden");
      document.getElementById("countdownText").innerText =
        `Hey ${userName}, only ${days} days, ${hours} hours, and ${minutes} minutes left for your birthday! 🎉`;

      document.getElementById("step3").classList.remove("hidden");
    }

    function showLetter() {
      document.getElementById("step3").classList.add("hidden");
      document.getElementById("letterSection").classList.remove("hidden");
    }

    function showLoveCard() {
      document.getElementById("letterSection").classList.add("hidden");
      document.getElementById("loveCard").classList.remove("hidden");
    }

    function startExchange() {
      document.getElementById("loveCard").classList.add("hidden");
      document.getElementById("finalScene").classList.remove("hidden");

      setTimeout(() => {
        document.getElementById("boy").style.transform = "translateX(100px)";
        document.getElementById("girl").style.transform = "translateX(-100px)";
      }, 1000);

      setTimeout(() => {
        document.getElementById("exchange").style.opacity = 1;
      }, 2000);
    }
  </script>
</body>
</html>
