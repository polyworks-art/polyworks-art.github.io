# polyworks-art.github.io
Website for Portfolio
<!doctype html>
<html lang="de">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Asset Breakdown</title>

<style>
  body {
    margin: 0;
    background: #111;
    font-family: Arial, sans-serif;
    color: white;
  }

  .viewer {
    max-width: 1200px;
    margin: auto;
    padding: 24px;
  }

  .compare {
    position: relative;
    width: 100%;
    overflow: hidden;
    aspect-ratio: 16 / 9;
    background: #222;
  }

  .compare img {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .top {
    width: 50%;
    overflow: hidden;
    position: absolute;
    inset: 0;
  }

  .top img {
    width: 100%;
    height: 100%;
    max-width: none;
  }

  .divider {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 50%;
    width: 2px;
    background: white;
    transform: translateX(-50%);
    pointer-events: none;
  }

  input[type="range"] {
    width: 100%;
    margin-top: 16px;
  }

  .buttons {
    display: flex;
    gap: 8px;
    margin-top: 16px;
    flex-wrap: wrap;
  }

  button {
    background: #222;
    color: white;
    border: 1px solid #555;
    padding: 8px 14px;
    cursor: pointer;
  }

  button:hover {
    background: #333;
  }
</style>
</head>

<body>
  <div class="viewer">
    <div class="compare">
      <img src="beauty.png" alt="Beauty Render">

      <div class="top" id="topLayer">
        <img id="overlayImage" src="wireframe.png" alt="Overlay Pass">
      </div>

      <div class="divider" id="divider"></div>
    </div>

    <input id="slider" type="range" min="0" max="100" value="50">

    <div class="buttons">
      <button onclick="setPass('wireframe.png')">Wireframe</button>
      <button onclick="setPass('normal.png')">Normal</button>
      <button onclick="setPass('albedo.png')">Albedo</button>
      <button onclick="setPass('roughness.png')">Roughness</button>
    </div>
  </div>

<script>
  const slider = document.getElementById("slider");
  const topLayer = document.getElementById("topLayer");
  const divider = document.getElementById("divider");
  const overlayImage = document.getElementById("overlayImage");

  slider.addEventListener("input", () => {
    const value = slider.value + "%";
    topLayer.style.width = value;
    divider.style.left = value;
  });

  function setPass(imagePath) {
    overlayImage.src = imagePath;
  }
</script>
</body>
</html>
