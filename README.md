<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8" />
  <title>Sadece sen okuyasın diye</title>
  <style>
    body {
      margin: 0;
      background: linear-gradient(to right, #ffefba, #ffffff);
      font-family: Arial, sans-serif;
      color: #333;
      text-align: center;
      overflow: hidden;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      position: relative;
    }
    .message {
      font-size: 1.6em;
      line-height: 1.6;
      opacity: 0;
      max-width: 90%;
      z-index: 10;
      position: relative;
      transition: opacity 2s ease-in-out;
    }
    .message.visible {
      opacity: 1;
    }
    .heart {
      width: 30px;
      height: 30px;
      position: absolute;
      background: #ff6b81;
      transform: rotate(45deg);
      animation: float 6s linear infinite;
      opacity: 0.8;
      border-radius: 6px 6px 0 0;
      z-index: 1;
    }
    .heart:before,
    .heart:after {
      content: "";
      width: 30px;
      height: 30px;
      background: #ff6b81;
      border-radius: 50%;
      position: absolute;
    }
    .heart:before { top: -15px; left: 0; }
    .heart:after { left: 15px; top: 0; }
    @keyframes float {
      0% { transform: translateY(100vh) rotate(45deg); opacity: 0.8; }
      100% { transform: translateY(-10vh) rotate(45deg); opacity: 0; }
    }
  </style>
</head>
<body>
  <div class="message" id="message">
    <p><strong>Hayat küçük sürprizlerle güzelleşir,</strong></p>
    <p><strong>sen de benim en büyük sürprizimsin.</strong></p>
  </div>
  <script>
    // Kalp animasyonları
    function createHeart() {
      const h = document.createElement('div');
      h.className = 'heart';
      h.style.left = Math.random() * 100 + 'vw';
      h.style.animationDuration = (Math.random() * 3 + 4) + 's';
      document.body.appendChild(h);
      setTimeout(() => h.remove(), 6000);
    }
    setInterval(createHeart, 400);

    // Yazının 3 saniye sonra görünmesi
    window.addEventListener('load', () => {
      setTimeout(() => {
        document.getElementById('message').classList.add('visible');
      }, 3000);
    });
  </script>
</body>
</html>
