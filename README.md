<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Birthday Swarnim 💖</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      background: radial-gradient(circle at top, #001133, #000010);
      color: white;
      font-family: 'Poppins', sans-serif;
      overflow: hidden;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      text-align: center;
      padding: 20px;
    }

    h1 {
      font-family: 'Great Vibes', cursive;
      font-size: clamp(2.5rem, 6vw, 4.5rem);
      color: #ff8ad9;
      text-shadow: 0 0 15px #ff6ec7, 0 0 30px #ff9ef0;
      animation: glow 3s ease-in-out infinite alternate;
      margin-bottom: 20px;
      line-height: 1.2;
    }

    @keyframes glow {
      from { text-shadow: 0 0 10px #ffb6f7, 0 0 20px #ff85d8; }
      to { text-shadow: 0 0 30px #ff6ec7, 0 0 50px #ffbdf5; }
    }

    .quote {
      width: 90%;
      max-width: 600px;
      font-size: clamp(1rem, 4vw, 1.4rem);
      line-height: 1.6;
      color: #f7c9ff;
      opacity: 0;
      transition: opacity 2s ease-in-out;
      min-height: 60px;
    }

    .quote.show {
      opacity: 1;
    }

    canvas {
      position: absolute;
      top: 0;
      left: 0;
      z-index: -1;
    }

    .balloon {
      position: absolute;
      bottom: -150px;
      width: 60px;
      height: 80px;
      border-radius: 50%;
      opacity: 0.9;
      animation: floatUp 6s ease-in-out forwards;
    }

    @keyframes floatUp {
      0% { transform: translateY(0); opacity: 1; }
      100% { transform: translateY(-120vh); opacity: 0; }
    }

    @keyframes confettiFall {
      0% { transform: translateY(0) rotate(0deg); opacity: 1; }
      100% { transform: translateY(100vh) rotate(360deg); opacity: 0; }
    }
  </style>
</head>
<body>
  <canvas id="bg"></canvas>

  <h1>Happy Birthday Swarnim 💖</h1>

  <div class="quote" id="quote"></div>

  <audio autoplay loop>
    <source src="https://cdn.pixabay.com/download/audio/2023/03/01/audio_d2e9b8a7b5.mp3?filename=birthday-song-14378.mp3" type="audio/mpeg">
  </audio>

  <script>
    // ❤️ Floating hearts background
    const canvas = document.getElementById('bg');
    const ctx = canvas.getContext('2d');
    let hearts = [];

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    for (let i = 0; i < 80; i++) {
      hearts.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        size: Math.random() * 8 + 3,
        speed: Math.random() * 1 + 0.5,
        color: `hsl(${Math.random() * 360}, 70%, 70%)`
      });
    }

    function animateHearts() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      for (let h of hearts) {
        ctx.beginPath();
        ctx.fillStyle = h.color;
        ctx.globalAlpha = 0.8;
        ctx.moveTo(h.x, h.y);
        ctx.bezierCurveTo(h.x - h.size / 2, h.y - h.size / 2, h.x - h.size, h.y + h.size / 3, h.x, h.y + h.size);
        ctx.bezierCurveTo(h.x + h.size, h.y + h.size / 3, h.x + h.size / 2, h.y - h.size / 2, h.x, h.y);
        ctx.fill();
        h.y -= h.speed;
        if (h.y < -10) h.y = canvas.height + 10;
      }
      requestAnimationFrame(animateHearts);
    }
    animateHearts();

    // 💬 Birthday quotes
    const quotes = [
      "🎉 Wishing you endless smiles and sunshine on your special day!",
      "🌸 May your heart be filled with happiness today and always.",
      "🎂 You are a gift to the world, Swarnim — never forget that!",
      "💖 Every year you shine brighter than before. Keep glowing!",
      "🌈 Here’s to dreams coming true and a life full of joy."
    ];

    let quoteIndex = 0;
    const quoteDiv = document.getElementById('quote');

    function showQuote() {
      quoteDiv.classList.remove('show');
      setTimeout(() => {
        quoteDiv.innerHTML = quotes[quoteIndex];
        quoteDiv.classList.add('show');
        quoteIndex = (quoteIndex + 1) % quotes.length;
      }, 1000);
    }

    showQuote();
    setInterval(showQuote, 5000);

    // 🎈 Balloons & Confetti
    function createBalloon() {
      const balloon = document.createElement('div');
      balloon.classList.add('balloon');
      balloon.style.left = Math.random() * window.innerWidth + 'px';
      balloon.style.background = `hsl(${Math.random() * 360}, 70%, 60%)`;
      document.body.appendChild(balloon);
      setTimeout(() => balloon.remove(), 6000);
    }

    function releaseBalloons(count = 15) {
      for (let i = 0; i < count; i++) {
        setTimeout(createBalloon, i * 300);
      }
    }

    function createConfetti() {
      const confetti = document.createElement('div');
      confetti.style.position = 'absolute';
      confetti.style.width = '8px';
      confetti.style.height = '8px';
      confetti.style.background = `hsl(${Math.random() * 360}, 80%, 60%)`;
      confetti.style.left = Math.random() * window.innerWidth + 'px';
      confetti.style.top = '-10px';
      confetti.style.opacity = 0.9;
      confetti.style.borderRadius = '50%';
      confetti.style.animation = 'confettiFall 3s linear forwards';
      document.body.appendChild(confetti);
      setTimeout(() => confetti.remove(), 3000);
    }

    function releaseConfetti(count = 100) {
      for (let i = 0; i < count; i++) {
        setTimeout(createConfetti, i * 15);
      }
    }

    window.onload = () => {
      releaseBalloons();
      releaseConfetti();
    };
  </script>
</body>
</html>
