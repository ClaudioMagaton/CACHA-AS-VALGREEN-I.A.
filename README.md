<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Quiz da Cachaça - Madeira Ideal</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
    }
    .hidden {
      display: none;
    }
    button {
      margin: 10px;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>Descubra a Madeira Ideal para sua Cachaça!</h1>
  <div id="quiz">
    <div class="question" id="question-1">
      <h2>Qual cor você prefere na cachaça?</h2>
      <button onclick="selectAnswer(1, 'Dourada')">Dourada</button>
      <button onclick="selectAnswer(1, 'Âmbar')">Âmbar</button>
      <button onclick="selectAnswer(1, 'Avermelhada')">Avermelhada</button>
      <button onclick="selectAnswer(1, 'Transparente')">Transparente</button>
    </div>

    <div class="question hidden" id="question-2">
      <h2>Qual sabor predominante você prefere?</h2>
      <button onclick="selectAnswer(2, 'Adocicado')">Adocicado</button>
      <button onclick="selectAnswer(2, 'Amadeirado')">Amadeirado</button>
      <button onclick="selectAnswer(2, 'Floral')">Floral</button>
      <button onclick="selectAnswer(2, 'Especiarias')">Especiarias</button>
    </div>

    <div class="question hidden" id="question-3">
      <h2>Qual o objetivo de uso da cachaça?</h2>
      <button onclick="selectAnswer(3, 'Pura')">Pura</button>
      <button onclick="selectAnswer(3, 'Coquetéis')">Coquetéis</button>
      <button onclick="selectAnswer(3, 'Harmonização')">Harmonização</button>
    </div>

    <div id="result" class="hidden">
      <h2>Resultado:</h2>
      <p id="recommendation"></p>
    </div>
  </div>

  <script>
    const answers = {};
    const recommendations = {
      // Combinando características e 20 tipos de madeira
      "Dourada-Adocicado-Pura": { madeira: "Carvalho", tempo: "12-18 meses" },
      "Dourada-Adocicado-Coquetéis": { madeira: "Amburana", tempo: "6-12 meses" },
      "Dourada-Amadeirado-Harmonização": { madeira: "Ipê", tempo: "12-24 meses" },
      "Âmbar-Amadeirado-Pura": { madeira: "Jatobá", tempo: "18-24 meses" },
      "Âmbar-Floral-Coquetéis": { madeira: "Pau-Rosa", tempo: "12-18 meses" },
      "Âmbar-Especiarias-Harmonização": { madeira: "Cedro", tempo: "12-18 meses" },
      "Avermelhada-Adocicado-Pura": { madeira: "Pau-Brasil", tempo: "18-24 meses" },
      "Avermelhada-Adocicado-Coquetéis": { madeira: "Jequitibá", tempo: "6-12 meses" },
      "Avermelhada-Floral-Harmonização": { madeira: "Freijó", tempo: "12-18 meses" },
      "Transparente-Adocicado-Pura": { madeira: "Amendoim", tempo: "6-12 meses" },
      "Transparente-Amadeirado-Coquetéis": { madeira: "Angelim Pedra", tempo: "12-18 meses" },
      "Transparente-Especiarias-Harmonização": { madeira: "Angelim Vermelho", tempo: "12-24 meses" },
      "Dourada-Floral-Pura": { madeira: "Guaiacá", tempo: "12-18 meses" },
      "Âmbar-Adocicado-Pura": { madeira: "Castanheira", tempo: "18-24 meses" },
      "Âmbar-Especiarias-Coquetéis": { madeira: "Garapeira", tempo: "12-18 meses" },
      "Transparente-Floral-Pura": { madeira: "Eucalipto", tempo: "6-12 meses" },
      "Transparente-Especiarias-Coquetéis": { madeira: "Sucupira", tempo: "12-18 meses" },
      "Avermelhada-Floral-Pura": { madeira: "Peroba", tempo: "12-18 meses" },
      "Avermelhada-Especiarias-Harmonização": { madeira: "Jacarandá", tempo: "18-24 meses" },
      "Dourada-Especiarias-Coquetéis": { madeira: "Mogno Africano", tempo: "12-18 meses" },
    };

    function selectAnswer(question, answer) {
      answers[question] = answer;

      document.getElementById(`question-${question}`).classList.add('hidden');
      const nextQuestion = document.getElementById(`question-${question + 1}`);
      if (nextQuestion) {
        nextQuestion.classList.remove('hidden');
      } else {
        showResult();
      }
    }

    function showResult() {
      const key = Object.values(answers).join('-');
      const recommendation = recommendations[key] || { madeira: "Indefinida", tempo: "Consulte um especialista." };
      
      document.getElementById('recommendation').innerText = 
        `Madeira recomendada: ${recommendation.madeira}\nTempo de maturação: ${recommendation.tempo}`;
      document.getElementById('result').classList.remove('hidden');
    }
  </script>
</body>
</html>
