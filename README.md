<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>For Titima ❤️</title>

<style>
  * { box-sizing: border-box; }
  body {
    margin: 0;
    height: 100vh;
    font-family: "Comic Sans MS", cursive, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(270deg, #ff9a9e, #fad0c4, #ffd1ff);
    background-size: 600% 600%;
    animation: gradient 10s ease infinite;
    overflow: hidden;
    cursor: url("https://emojiapi.dev/api/v1/red_heart/32.png"), auto;
  }

  @keyframes gradient {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  .card {
    background: white;
    padding: 30px 40px;
    border-radius: 20px;
    text-align: center;
    box-shadow: 0 20px 40px rgba(0,0,0,0.2);
    position: relative;
  }

  h1 {
    color: #ff4d6d;
    margin-bottom: 20px;
  }

  button {
    font-size: 18px;
    padding: 12px 24px;
    border: none;
    border-radius: 30px;
    cursor: pointer;
    position: absolute;
  }

  #yes {
    background: #ff4d6d;
    color: white;
    left: 50%;
    transform: translateX(-120%);
    animation: pulse 1.5s infinite;
  }

  @keyframes pulse {
    0% { box-shadow: 0 0 0 0 rgba(255,77,109,0.6); }
    70% { box-shadow: 0 0 0 20px rgba(255,77,109,0); }
    100% { box-shadow: 0 0 0 0 rgba(255,77,109,0); }
  }

  #no {
    background: #ccc;
    color: #333;
    left: 50%;
    transform: translateX(20%);
  }

  .heart {
    position: fixed;
    font-size: 20px;
    animation: float 6s linear infinite;
  }

  @keyframes float {
    from { transform: translateY(100vh); opacity: 1; }
    to { transform: translateY(-10vh); opacity: 0; }
  }

  .confetti {
    position: fixed;
    font-size: 24px;
    animation: explode 2s ease-out forwards;
  }

  @keyframes explode {
    to {
      transform: translate(var(--x), var(--y)) rotate(720deg);
      opacity: 0;
    }
  }
</style>
</head>

<body>

<div class="card">
  <h1 id="message">Titima, will you be my Valentine? ❤️</h1>
  <button id="yes">YES 💖</button>
  <button id="no">NO 😜</button>
</div>

<script>
  const noBtn = document.getElementById("no");
  const yesBtn = document.getElementById("yes");
  const msg = document.getElementById("message");

  let attempts = 0;
  const messages = [
    "Titima, will you be my Valentine? ❤️",
    "Are you suuuuure? 😳",
    "Please? Pretty please? 🥺",
    "I won't give up on you 😤❤️",
    "That button is shy 😈",
    "Just say YES already 😘"
  ];

  noBtn.addEventListener("mouseover", () => {
    attempts++;
    msg.textContent = messages[Math.min(attempts, messages.length - 1)];

    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 100);
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
  });

  yesBtn.addEventListener("click", () => {
    msg.textContent = "YAAAAY 💖💖💖 I knew it, Titima!";
    createConfetti();
  });

  function createConfetti() {
    for (let i = 0; i < 40; i++) {
      const conf = document.createElement("div");
      conf.className = "confetti";
      conf.textContent = "💖";
      conf.style.left = "50%";
      conf.style.top = "50%";
      conf.style.setProperty("--x", (Math.random() * 600 - 300) + "px");
      conf.style.setProperty("--y", (Math.random() * 600 - 300) + "px");
      document.body.appendChild(conf);
      setTimeout(() => conf.remove(), 2000);
    }
  }

  // floating hearts
  setInterval(() => {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.textContent = "❤️";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = (Math.random() * 3 + 3) + "s";
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 6000);
  }, 400);
</script>

</body>
</html>
