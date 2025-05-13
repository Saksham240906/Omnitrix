<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Omnitrix Transformation</title>
  <style>
    :root {
      --dark-color: #000;
    }

    body {
      margin: 0;
      padding: 0;
      position: relative;
      min-height: 100vh;
      overflow: hidden;
      font-family: Arial, sans-serif;
      color: white;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .night {
      position: fixed;
      left: 50%;
      top: 0;
      transform: translateX(-50%);
      width: 100%;
      height: 100%;
      filter: blur(0.1vmin);
      background-image: radial-gradient(ellipse at top, transparent 0%, var(--dark-color)),
        radial-gradient(ellipse at bottom, var(--dark-color), rgba(145, 233, 255, 0.2)),
        repeating-linear-gradient(220deg, #000 0px, #000 19px, transparent 19px, transparent 22px),
        repeating-linear-gradient(189deg, #000 0px, #000 19px, transparent 19px, transparent 22px),
        repeating-linear-gradient(148deg, #000 0px, #000 19px, transparent 19px, transparent 22px);
      z-index: -1;
    }

    h1 {
      text-align: center;
      font-size: 4rem;
      margin-top: 20px;
      color: limegreen;
      text-shadow: 0 0 10px lime;
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      z-index: 10;
    }

    .container {
      position: relative;
      width: 600px;
      height: 600px;
      margin-top: 250px;
      display: flex;
      justify-content: center;
      align-items: center;
      transition: transform 0.5s ease;
    }

    .omnitrix {
      position: absolute;
      width: 150px;
      height: 150px;
      background-image: url(omnitrix.png);
      background-size: cover;
      background-position: center;
      border-radius: 50%;
      border: 5px solid black;
      cursor: pointer;
      z-index: 10;
      box-shadow: 0 0 15px lime;
      transition: transform 0.3s ease;
    }

    .omnitrix:hover {
      transform: scale(1.2);
    }

    .alien {
      position: absolute;
      width: 90px;
      height: 90px;
      background-size: cover;
      background-position: center;
      border-radius: 50%;
      border: 2px solid white;
      box-shadow: 0 0 10px limegreen;
      cursor: pointer;
      transition: transform 0.3s ease;
    }

    .alien:hover {
      transform: scale(1.3);
    }

    .alien-details-container {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 300px;
      height: 400px;
      background-color: rgba(0, 0, 0, 0.9);
      border-radius: 15px;
      border: 2px solid lime;
      display: none;
      color: white;
      text-align: center;
      z-index: 1000;
      padding: 20px;
      transition: all 0.5s ease;
    }

    .alien-details-container img {
      max-width: 100%;
      max-height: 200px;
      border: 2px solid lime;
      margin-bottom: 20px;
    }

    .alien-details-container button {
      padding: 10px 20px;
      background: limegreen;
      border: none;
      color: black;
      border-radius: 5px;
      cursor: pointer;
    }

    .alien-details-container button:hover {
      background: white;
      color: black;
    }

    .ben10-info-box {
      position: fixed;
      right: 20px;
      top: 100px;
      width: 300px;
      background-color: rgba(0, 0, 0, 0.8);
      border: 2px solid limegreen;
      border-radius: 10px;
      padding: 20px;
      color: white;
      z-index: 20;
      font-size: 1rem;
      line-height: 1.5;
      box-shadow: 0 0 10px limegreen;
    }

    .ben10-info-box h2 {
      margin-top: 0;
      color: lime;
    }
  </style>
</head>
<body>
  <div class="night"></div>

  <h1>OMNITRIX</h1>

  <div class="container">
    <div class="omnitrix" onclick="showOmnitrixDetails()"></div>

    <div class="alien" id="alien0" onclick="showAlienDetails(0)"></div>
    <div class="alien" id="alien1" onclick="showAlienDetails(1)"></div>
    <div class="alien" id="alien2" onclick="showAlienDetails(2)"></div>
    <div class="alien" id="alien3" onclick="showAlienDetails(3)"></div>
    <div class="alien" id="alien4" onclick="showAlienDetails(4)"></div>
    <div class="alien" id="alien5" onclick="showAlienDetails(5)"></div>
    <div class="alien" id="alien6" onclick="showAlienDetails(6)"></div>
    <div class="alien" id="alien7" onclick="showAlienDetails(7)"></div>
    <div class="alien" id="alien8" onclick="showAlienDetails(8)"></div>
    <div class="alien" id="alien9" onclick="showAlienDetails(9)"></div>
  </div>

  <div class="alien-details-container" id="alienDetailsBox">
    <img id="alienImage" src="" alt="Alien Image" />
    <h2 id="alienName"></h2>
    <p id="alienDescription"></p>
    <button onclick="closeAlienDetails()">Close</button>
  </div>

  <div class="ben10-info-box">
    <h2>About Ben 10</h2>
    <p><strong>Ben 10</strong> is an American animated television series created by the group "Man of Action" and produced by Cartoon Network Studios.</p>
    <p>It follows the story of <strong>Ben Tennyson</strong>, a boy who discovers a mysterious alien device called the <strong>Omnitrix</strong>, allowing him to transform into different powerful alien beings.</p>
    <p>The show is known for its exciting action, sci-fi themes, and the wide variety of aliens Ben can turn into.</p>
  </div>

  <script>
    const aliens = [
      'Heatblast.png', 'Fourarms.png', 'XLR8.png', 'Diamondhead.png', 'Upgrade.png',
      'Ghostfreak.png', 'Wildmutt.png', 'Stinkyfly.png', 'Ripjaws.png', 'Greymatter.png'
    ];

    const alienDetails = [
      { name: "Heatblast", description: "Fire powers" },
      { name: "Four Arms", description: "Super strength" },
      { name: "XLR8", description: "Super speed" },
      { name: "Diamondhead", description: "Crystal body" },
      { name: "Upgrade", description: "Tech assimilation" },
      { name: "Ghostfreak", description: "Intangibility" },
      { name: "Wildmutt", description: "Enhanced senses" },
      { name: "Stinkfly", description: "Flight and slime" },
      { name: "Ripjaws", description: "Aquatic abilities" },
      { name: "Grey Matter", description: "Super intelligence" }
    ];

    const omnitrixDetails = {
      name: "Omnitrix",
      description: "An alien device containing DNA of 10+ aliens allowing transformation.",
      image: "omnitrix.png"
    };

    function positionAliens() {
      const radius = 220;
      for (let i = 0; i < 10; i++) {
        const angle = (i / 10) * 2 * Math.PI;
        const x = 300 + radius * Math.cos(angle) - 45;
        const y = 300 + radius * Math.sin(angle) - 45;
        const el = document.getElementById(`alien${i}`);
        el.style.left = `${x}px`;
        el.style.top = `${y}px`;
        el.style.backgroundImage = `url('${aliens[i]}')`;
      }
    }

    function rotateAliens() {
      let angle = 0;
      setInterval(() => {
        angle += 1;
        const radius = 220;
        for (let i = 0; i < 10; i++) {
          const a = angle * Math.PI / 180 + (i / 10) * 2 * Math.PI;
          const x = 300 + radius * Math.cos(a) - 45;
          const y = 300 + radius * Math.sin(a) - 45;
          const el = document.getElementById(`alien${i}`);
          el.style.left = `${x}px`;
          el.style.top = `${y}px`;
        }
      }, 30);
    }

    function showOmnitrixDetails() {
      const box = document.getElementById("alienDetailsBox");
      document.getElementById("alienImage").src = omnitrixDetails.image;
      document.getElementById("alienName").textContent = omnitrixDetails.name;
      document.getElementById("alienDescription").textContent = omnitrixDetails.description;

      box.style.left = "50%";
      box.style.transform = "translate(-50%, -50%)";

      setTimeout(() => {
        box.style.left = "0";
        box.style.transform = "translateY(-50%)";
      }, 100);
      box.style.display = "block";
    }

    function showAlienDetails(index) {
      const detail = alienDetails[index];
      const box = document.getElementById("alienDetailsBox");

      document.getElementById("alienImage").src = aliens[index];
      document.getElementById("alienName").textContent = detail.name;
      document.getElementById("alienDescription").textContent = detail.description;

      box.style.left = "50%";
      box.style.transform = "translate(-50%, -50%)";

      setTimeout(() => {
        box.style.left = "0";
        box.style.transform = "translateY(-50%)";
      }, 100);
      box.style.display = "block";
    }

    function closeAlienDetails() {
      document.getElementById("alienDetailsBox").style.display = "none";
    }

    positionAliens();
    rotateAliens();
  </script>
</body>
</html>
