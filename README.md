<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Anamitra Roy - Matrix Snake</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background-color: black;
      color: #00FF41;
      font-family: 'Courier New', monospace;
      overflow: hidden;
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 0;
    }

    .container {
      position: relative;
      z-index: 2;
      padding: 20px;
      max-width: 1000px;
      margin: auto;
    }

    a, h1, h3, p, li {
      color: #00FF41;
    }

    img {
      vertical-align: middle;
    }

    /* Snake Styling */
    .snake-dot {
      width: 20px;
      height: 20px;
      background-color: #00FF41;
      box-shadow: 0 0 10px #00FF41;
      position: absolute;
      top: 100px;
      z-index: 1;
    }
  </style>
</head>
<body>

<canvas id="matrix"></canvas>

<div class="container">
  <h1 align="center">Hi 👋, I'm Anamitra Roy</h1>
  <h3 align="center">A passionate Software Engineer from India</h3>

  <ul>
    <li>🔭 I’m currently working on <strong>Personal projects</strong></li>
    <li>👯 I’m collaborating with coders — <strong>10 Major projects done</strong></li>
    <li>💬 Ask me about <strong>Web Development, Data Science, AWS</strong></li>
    <li>📫 Reach me at <strong>anamitraroy2206@gmail.com</strong></li>
    <li>⚡ Fun fact: <strong>It’s all 0’s and 1’s</strong></li>
  </ul>

  <h3>Connect with me:</h3>
  <p>
    <a href="https://www.linkedin.com/in/anamitra-roy-6937a42a5/" target="_blank">
      <img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" width="40" height="30" />
    </a>
  </p>

  <h3>Languages and Tools:</h3>
  <!-- Paste your tool icons here (trimmed for brevity) -->
  <!-- START tool icons section -->
  <p>
    <a href="https://angular.io" target="_blank"><img src="https://angular.io/assets/images/logos/angular/angular.svg" width="40" height="40"/></a>
    <a href="https://aws.amazon.com" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" width="40" height="40"/></a>
    <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" width="40" height="40"/></a>
    <a href="https://reactjs.org/" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" width="40" height="40"/></a>
    <a href="https://www.python.org" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" width="40" height="40"/></a>
    <!-- Add more as needed -->
  </p>
  <!-- END tool icons section -->

  <p><img align="center" src="https://github-readme-stats.vercel.app/api/top-langs?username=anamitraroy22&show_icons=true&locale=en&layout=compact" alt="GitHub stats" /></p>
</div>

<!-- Matrix Background Script -->
<script>
  const canvas = document.getElementById("matrix");
  const ctx = canvas.getContext("2d");

  canvas.height = window.innerHeight;
  canvas.width = window.innerWidth;

  const matrixChars = "アァイィウエエオカキクケコサシスセソタチツテトナニヌネノ";
  const fontSize = 16;
  const columns = canvas.width / fontSize;

  const drops = Array.from({ length: columns }).fill(1);

  function drawMatrix() {
    ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    ctx.fillStyle = "#00FF41";
    ctx.font = fontSize + "px monospace";

    for (let i = 0; i < drops.length; i++) {
      const text = matrixChars[Math.floor(Math.random() * matrixChars.length)];
      ctx.fillText(text, i * fontSize, drops[i] * fontSize);

      if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
        drops[i] = 0;
      }

      drops[i]++;
    }
  }

  setInterval(drawMatrix, 33);
</script>

<!-- Matrix Snake Script -->
<script>
  const snakeLength = 30;
  const snakeDots = [];

  for (let i = 0; i < snakeLength; i++) {
    const dot = document.createElement("div");
    dot.className = "snake-dot";
    dot.style.left = `${-i * 22}px`;
    document.body.appendChild(dot);
    snakeDots.push(dot);
  }

  let snakeX = 0;
  setInterval(() => {
    snakeX += 4;
    for (let i = 0; i < snakeDots.length; i++) {
      const dot = snakeDots[i];
      dot.style.left = `${snakeX - i * 22}px`;
    }
    if (snakeX > window.innerWidth + snakeLength * 22) {
      snakeX = -snakeLength * 22;
    }
  }, 40);
</script>

</body>
</html>
