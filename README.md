# Videogena
New video gena
index.html 
<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8" />
  <title>AI Video Generator</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <h1>🎬 AI Video Script Generator</h1>

    <input id="topic" type="text" placeholder="ভিডিও টপিক লিখুন" />
    <input id="duration" type="number" placeholder="সময় (মিনিট)" />

    <button onclick="generate()">Generate Script</button>

    <textarea id="output" placeholder="স্ক্রিপ্ট এখানে দেখাবে"></textarea>
  </div>

  <script src="script.js"></script>
</body>
</html>

index.css
body {
  font-family: sans-serif;
  background: #111;
  color: #fff;
}
.container {
  max-width: 500px;
  margin: 50px auto;
}
input, textarea, button {
  width: 100%;
  margin: 10px 0;
  padding: 10px;
}
button {
  background: #00ff99;
  border: none;
}

index.javascript 
async function generate() {
  const topic = document.getElementById("topic").value;
  const duration = document.getElementById("duration").value;

  const res = await fetch("http://localhost:5000/generate-script", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ topic, duration })
  });

  const data = await res.json();
  document.getElementById("output").value = data.script;
}
