# mi-corazon

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Corazón "I love you"</title>
  <style>
    body {
      margin: 0;
      background-color: black;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
    }
    canvas {
      background-color: black;
    }
  </style>
</head>
<body>

  <canvas id="heartCanvas"></canvas>

  <script>
    const canvas = document.getElementById('heartCanvas');
    const ctx = canvas.getContext('2d');

    // Ajustar resolución del canvas
    const width = window.innerWidth;
    const height = window.innerHeight;
    canvas.width = width;
    canvas.height = height;

    const centerX = width / 2;
    const centerY = height / 2;

    ctx.fillStyle = "#ffb6c1";
    ctx.font = "bold 8px Arial";
    ctx.textAlign = "center";
    ctx.textBaseline = "middle";

    // Dibujar el corazón usando exactamente las mismas fórmulas
    for (let scale = 11; scale < 17; scale++) {
      for (let i = 0; i < 120; i++) {
        const t = i * (2 * Math.PI) / 120;
        
        const x = 16 * Math.pow(Math.sin(t), 3);
        const y = 13 * Math.cos(t) - 5 * Math.cos(2 * t) - 2 * Math.cos(3 * t) - Math.cos(4 * t);

        // En canvas la dirección 'y' está invertida respecto a turtle
        const pixelX = centerX + (x * scale);
        const pixelY = centerY - (y * scale);

        ctx.fillText("I love you", pixelX, pixelY);
      }
    }
  </script>

</body>
</html>
