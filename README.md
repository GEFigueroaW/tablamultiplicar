<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>¡Multiplica con Animalitos!</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- Estilos -->
  <style>
    body {
      font-family: 'Comic Sans MS', cursive, sans-serif;
      background: #fce4ec;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      color: #333;
    }

    h1 {
      color: #e91e63;
      text-align: center;
      margin-bottom: 10px;
    }

    #game-container {
      background-color: #fff;
      padding: 20px;
      border-radius: 20px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.2);
      text-align: center;
      width: 90%;
      max-width: 400px;
    }

    #animal {
      width: 120px;
      height: 120px;
      object-fit: contain;
      margin-bottom: 15px;
    }

    #question {
      font-size: 24px;
      margin: 10px 0;
    }

    input[type="number"] {
      padding: 10px;
      font-size: 20px;
      width: 100px;
      text-align: center;
      border: 2px solid #e91e63;
      border-radius: 10px;
      margin: 10px 0;
    }

    button {
      background-color: #e91e63;
      color: white;
      padding: 10px 20px;
      font-size: 18px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      margin-top: 10px;
    }

    button:hover {
      background-color: #d81b60;
    }

    #feedback {
      font-size: 20px;
      margin-top: 15px;
      font-weight: bold;
    }

    .correct {
      color: green;
    }

    .incorrect {
      color: red;
    }
  </style>
</head>
<body>
  <h1>¡Multiplica con Animalitos!</h1>
  <div id="game-container">
    <img id="animal" src="" alt="Animal divertido">
    <div id="question">¿Cuánto es 2 x 3?</div>
    <input type="number" id="answer" placeholder="Tu respuesta">
    <br>
    <button onclick="checkAnswer()">Verificar</button>
    <div id="feedback"></div>
  </div>

  <!-- Lógica JavaScript -->
  <script>
    const animals = [
      { name: 'Conejito', img: 'https://cdn.pixabay.com/photo/2017/01/31/15/49/rabbit-2027366_1280.png' },
      { name: 'Perrito', img: 'https://cdn.pixabay.com/photo/2017/01/31/15/46/dog-2027365_1280.png' },
      { name: 'Gatito', img: 'https://cdn.pixabay.com/photo/2017/01/31/15/46/cat-2027364_1280.png' },
      { name: 'Elefante', img: 'https://cdn.pixabay.com/photo/2016/04/01/10/26/elephant-1298157_1280.png' },
      { name: 'Zorrito', img: 'https://cdn.pixabay.com/photo/2021/01/28/09/23/fox-5956961_1280.png' }
    ];

    let num1, num2, correctAnswer;

    function getRandomInt(min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min;
    }

    function newQuestion() {
      const animal = animals[getRandomInt(0, animals.length - 1)];
      document.getElementById('animal').src = animal.img;
      document.getElementById('animal').alt = animal.name;

      num1 = getRandomInt(1, 10);
      num2 = getRandomInt(1, 10);
      correctAnswer = num1 * num2;

      document.getElementById('question').textContent = `¿Cuánto es ${num1} x ${num2}?`;
      document.getElementById('answer').value = '';
      document.getElementById('feedback').textContent = '';
      document.getElementById('feedback').className = '';
    }

    function checkAnswer() {
      const userAnswer = parseInt(document.getElementById('answer').value);
      const feedback = document.getElementById('feedback');
      if (userAnswer === correctAnswer) {
        feedback.textContent = '¡Muy bien! 🎉';
        feedback.className = 'correct';
        setTimeout(newQuestion, 1500);
      } else {
        feedback.textContent = '¡Inténtalo de nuevo! 😅';
        feedback.className = 'incorrect';
      }
    }

    // Iniciar el juego
    window.onload = newQuestion;
  </script>
</body>
</html>
