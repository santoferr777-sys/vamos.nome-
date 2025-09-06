# vamos.nome-
index.html
style.css
script.js
<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8">
  <title>Cadavere Squisito Online</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Cadavere Squisito Online</h1>
  <div id="game">
    <p id="instructions">Scrivi la tua parte della frase:</p>
    <textarea id="inputText" placeholder="Scrivi qui..." rows="3"></textarea>
    <button id="submitBtn">Invia</button>
  </div>
  <div id="result" style="display:none;">
    <h2>Frase completata:</h2>
    <p id="finalPhrase"></p>
    <button onclick="location.reload()">Gioca ancora</button>
  </div>
  <script src="script.js"></script>
</body>
</html>
body {
  font-family: sans-serif;
  text-align: center;
  padding: 20px;
  background-color: #f7f7f7;
}
textarea {
  width: 80%;
  margin-top: 10px;
  font-size: 1.1em;
}
button {
  margin-top: 10px;
  padding: 10px 20px;
  font-size: 1em;
}
let currentTurn = 0;
const maxTurns = 3;
let sentenceParts = [];

const input = document.getElementById("inputText");
const submitBtn = document.getElementById("submitBtn");
const instructions = document.getElementById("instructions");
const gameDiv = document.getElementById("game");
const resultDiv = document.getElementById("result");
const finalPhrase = document.getElementById("finalPhrase");

const turnInstructions = [
  "Scrivi il SOGGETTO (es. 'Il cane')",
  "Scrivi il VERBO (es. 'mangia')",
  "Scrivi il COMPLEMENTO (es. 'una mela gigante')"
];

instructions.textContent = turnInstructions[currentTurn];

submitBtn.addEventListener("click", () => {
  const text = input.value.trim();
  if (text === "") return;

  sentenceParts.push(text);
  input.value = "";
  currentTurn++;

  if (currentTurn < maxTurns) {
    instructions.textContent = turnInstructions[currentTurn];
  } else {
    gameDiv.style.display = "none";
    resultDiv.style.display = "block";
    finalPhrase.textContent = sentenceParts.join(" ");
  }
});
