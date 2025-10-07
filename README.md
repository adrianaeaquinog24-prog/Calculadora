<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🔬 Calculadora Genética Escolar</title>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #a2d2ff, #cdb4db);
      color: #333;
      text-align: center;
      padding: 40px;
    }

    h1 {
      color: #4a148c;
      font-size: 2.2em;
      margin-bottom: 10px;
    }

    h2 {
      color: #6a1b9a;
    }

    .container {
      background: white;
      padding: 25px;
      border-radius: 20px;
      box-shadow: 0px 8px 25px rgba(0, 0, 0, 0.2);
      max-width: 700px;
      margin: auto;
    }

    .trait-section {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-bottom: 30px;
    }

    select {
      padding: 10px;
      margin: 10px;
      border-radius: 10px;
      border: 2px solid #ce93d8;
      background-color: #f3e5f5;
      font-size: 1em;
    }

    button {
      background-color: #7b1fa2;
      color: white;
      padding: 12px 20px;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      font-size: 1.1em;
      transition: 0.3s;
    }

    button:hover {
      background-color: #9c27b0;
      transform: scale(1.05);
    }

    .result-card {
      background: #ede7f6;
      border-radius: 15px;
      padding: 20px;
      margin-top: 25px;
      box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
      font-size: 1.1em;
      animation: fadeIn 0.8s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    img {
      width: 80px;
      margin-top: 10px;
    }

    .trait-label {
      font-weight: bold;
      color: #4a148c;
      margin-top: 10px;
    }

  </style>
</head>
<body>
  <div class="container">
    <h1>🧬 Calculadora Genética Escolar</h1>
    <p>Descubre qué rasgos podría tener un hijo combinando los de sus padres.</p>

    <div class="trait-section">
      <h2>👩 Rasgos del Padre</h2>
      <label class="trait-label">Color de ojos:</label>
      <select id="ojosPadre">
        <option value="marrones">Marrones</option>
        <option value="verdes">Verdes</option>
        <option value="azules">Azules</option>
      </select>

      <label class="trait-label">Color de pelo:</label>
      <select id="peloPadre">
        <option value="negro">Negro</option>
        <option value="castaño">Castaño</option>
        <option value="rubio">Rubio</option>
      </select>

      <label class="trait-label">Altura:</label>
      <select id="alturaPadre">
        <option value="alto">Alto</option>
        <option value="bajo">Bajo</option>
      </select>

      <img src="https://cdn-icons-png.flaticon.com/512/4140/4140048.png" alt="Padre">
    </div>

    <div class="trait-section">
      <h2>👩‍🦰 Rasgos de la Madre</h2>
      <label class="trait-label">Color de ojos:</label>
      <select id="ojosMadre">
        <option value="marrones">Marrones</option>
        <option value="verdes">Verdes</option>
        <option value="azules">Azules</option>
      </select>

      <label class="trait-label">Color de pelo:</label>
      <select id="peloMadre">
        <option value="negro">Negro</option>
        <option value="castaño">Castaño</option>
        <option value="rubio">Rubio</option>
      </select>

      <label class="trait-label">Altura:</label>
      <select id="alturaMadre">
        <option value="alto">Alta</option>
        <option value="bajo">Baja</option>
      </select>

      <img src="https://cdn-icons-png.flaticon.com/512/4140/4140051.png" alt="Madre">
    </div>

    <button onclick="calcular()">🔍 Calcular resultado genético</button>

    <div id="resultado" class="result-card" style="display:none;"></div>
  </div>

  <script>
    function calcular() {
      const ojosP = document.getElementById('ojosPadre').value;
      const ojosM = document.getElementById('ojosMadre').value;
      const peloP = document.getElementById('peloPadre').value;
      const peloM = document.getElementById('peloMadre').value;
      const alturaP = document.getElementById('alturaPadre').value;
      const alturaM = document.getElementById('alturaMadre').value;

      let resultado = "<h3>👶 Posibles rasgos del hijo:</h3>";

      // Color de ojos
      if (ojosP === "marrones" || ojosM === "marrones") {
        resultado += "<p>👁️ <b>Color de ojos:</b> 75% marrones, 15% verdes, 10% azules</p>";
      } else if (ojosP === "verdes" || ojosM === "verdes") {
        resultado += "<p>👁️ <b>Color de ojos:</b> 50% verdes, 30% azules, 20% marrones</p>";
      } else {
        resultado += "<p>👁️ <b>Color de ojos:</b> 80% azules, 20% verdes</p>";
      }

      // Color de pelo
      if (peloP === "negro" || peloM === "negro") {
        resultado += "<p>💇‍♂️ <b>Color de pelo:</b> 70% negro, 20% castaño, 10% rubio</p>";
      } else if (peloP === "castaño" || peloM === "castaño") {
        resultado += "<p>💇‍♀️ <b>Color de pelo:</b> 60% castaño, 25% rubio, 15% negro</p>";
      } else {
        resultado += "<p>💛 <b>Color de pelo:</b> 80% rubio, 20% castaño</p>";
      }

      // Altura
      if (alturaP === "alto" && alturaM === "alto") {
        resultado += "<p>📏 <b>Altura:</b> 80% alto, 20% bajo</p>";
      } else if (alturaP === "bajo" && alturaM === "bajo") {
        resultado += "<p>📏 <b>Altura:</b> 80% bajo, 20% alto</p>";
      } else {
        resultado += "<p>📏 <b>Altura:</b> 50% alto, 50% bajo</p>";
      }

      document.getElementById('resultado').innerHTML = resultado;
      document.getElementById('resultado').style.display = 'block';
    }
  </script>
</body>
</html>
