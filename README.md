<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>京女生診断ゲーム</title>
  <style>
    body {
      font-family: sans-serif;
      background-color: #fefefe;
      text-align: center;
      padding: 2em;
    }
    .question, .result, #start-screen {
      display: none;
    }
    .active {
      display: block;
    }
    button {
      display: block;
      margin: 1em auto;
      padding: 1em 2em;
      font-size: 1em;
      background-color: #ffb6c1;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
    .result {
      font-size: 1.3em;
      margin-top: 2em;
    }
    a.button-link {
      display: inline-block;
      margin-top: 1.5em;
      background-color: #f08080;
      color: white;
      padding: 0.8em 1.5em;
      border-radius: 8px;
      text-decoration: none;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>京女生診断！あなたにぴったりの部活は？</h1>

  <div id="start-screen" class="active">
    <p>あなたにぴったりの部活を診断しよう♪</p>
    <button onclick="startGame()">はじめる</button>
  </div>

  <div id="question-container">
    <div class="question">
      <p>Q1. 放課後はどう過ごしたい？</p>
      <button onclick="nextQuestion()">おしゃべりしながらゆるっと活動したい</button>
      <button onclick="nextQuestion()">ひとりで黙々と打ち込める時間がほしい</button>
      <button onclick="nextQuestion()">みんなで目標に向かってがんばりたい</button>
    </div>

    <div class="question">
      <p>Q2. 興味があるものは？</p>
      <button onclick="nextQuestion()">音楽</button>
      <button onclick="nextQuestion()">楽しいこと</button>
      <button onclick="nextQuestion()">ちょっと人と違うこと</button>
    </div>

    <div class="question">
      <p>Q3. どんな雰囲気の部活がいい？</p>
      <button onclick="nextQuestion()">優しい先輩がいる部活</button>
      <button onclick="nextQuestion()">初心者歓迎の部活</button>
      <button onclick="nextQuestion()">自分のペースで続けられる部活</button>
    </div>

    <div class="question">
      <p>Q4. 音楽経験はある？</p>
      <button onclick="showResult(true)">ある！</button>
      <button onclick="showResult(false)">ない！</button>
    </div>
  </div>

  <div id="result" class="result">
    <p>＼あなたにぴったりの部活は…／</p>
    <h2>🎶 マンドリンオーケストラ部！ 🎶</h2>
    <p id="music-message"></p>
    
    <p style="margin-top: 2em;">
      🎵 <strong>興味がある人はこちらから楽器体験に応募しよう！</strong><br>
      <a href="https://docs.google.com/forms/d/1Kgp0YwwheMONJPUA0qfHBguXWYVfGkEaKyF_hlECfoQ/viewform?edit_requested=true"
         target="_blank"
         class="button-link">🎹 楽器体験フォームはこちら</a>
    </p>
  </div>

  <script>
    let current = 0;
    const questions = document.querySelectorAll('.question');
    const startScreen = document.getElementById('start-screen');
    const resultScreen = document.getElementById('result');
    const musicMessage = document.getElementById('music-message');

    function startGame() {
      startScreen.classList.remove('active');
      questions[current].classList.add('active');
    }

    function nextQuestion() {
      if (current < questions.length - 1) {
        questions[current].classList.remove('active');
        current++;
        questions[current].classList.add('active');
      }
    }

    function showResult(hasExperience) {
      questions[current].classList.remove('active');
      resultScreen.classList.add('active');

      if (hasExperience) {
        musicMessage.textContent = "音楽経験があるあなたはさらに楽しめます！大学で新しいことに挑戦してみませんか？新しい音楽仲間と一緒に奏でよう♪";
      } else {
        musicMessage.textContent = "音楽経験がなくても、安心して上達できるマンドリンオーケストラ部がおすすめ！";
      }
    }
  </script>
</body>
</html>
