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
    .screen {
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
      font-size: 1.5em;
      margin-top: 2em;
    }
    .share-buttons a {
      display: inline-block;
      margin: 10px;
      padding: 0.5em 1em;
      background-color: #1DA1F2;
      color: white;
      border-radius: 5px;
      text-decoration: none;
      font-size: 0.9em;
    }
    .share-buttons a:hover {
      opacity: 0.9;
    }
  </style>
</head>
<body>
  <h1>京女生診断！あなたにぴったりの部活は？</h1>

  <!-- Start Screen -->
  <div id="start-screen" class="screen active">
    <p>簡単な質問に答えるだけで、あなたにぴったりの部活がわかるよ！</p>
    <button onclick="startQuiz()">診断スタート！</button>
  </div>

  <!-- Questions -->
  <div id="question-container">
    <div class="screen question">
      <p>Q1. 放課後はどう過ごしたい？</p>
      <button onclick="nextQuestion()">おしゃべりしながらゆるっと活動したい</button>
      <button onclick="nextQuestion()">ひとりで黙々と打ち込める時間がほしい</button>
      <button onclick="nextQuestion()">みんなで目標に向かってがんばりたい</button>
    </div>

    <div class="screen question">
      <p>Q2. 興味があるものは？</p>
      <button onclick="nextQuestion()">音楽</button>
      <button onclick="nextQuestion()">楽しいこと</button>
      <button onclick="nextQuestion()">ちょっと人と違うこと</button>
    </div>

    <div class="screen question">
      <p>Q3. どんな雰囲気の部活がいい？</p>
      <button onclick="nextQuestion()">優しい先輩がいる部活</button>
      <button onclick="nextQuestion()">初心者歓迎の部活</button>
      <button onclick="nextQuestion()">自分のペースで続けられる部活</button>
    </div>

    <div class="screen question">
      <p>Q4. 音楽経験はある？</p>
      <button onclick="showResult('yes')">ある！</button>
      <button onclick="showResult('no')">ないけど興味ある！</button>
    </div>
  </div>

  <!-- Result -->
<div id="result" class="result">
  <p>＼あなたにぴったりの部活は…／</p>
  <h2 id="club-name">🎶 マンドリンオーケストラ部！ 🎶</h2>
  <p id="club-message">初心者も大歓迎！あたたかい仲間と一緒に音楽を楽しもう♪</p>

  <!-- 🎯 応募フォームリンク -->
  <p style="margin-top: 2em;">
    🎵 <strong>興味がある人はこちらから楽器体験に応募しよう！</strong><br>
    <a href="https://docs.google.com/forms/d/1Kgp0YwwheMONJPUA0qfHBguXWYVfGkEaKyF_hlECfoQ/viewform?edit_requested=true" 
       target="_blank"
       style="display: inline-block; margin-top: 1em; background-color: #f08080; color: white; padding: 0.8em 1.5em; border-radius: 8px; text-decoration: none;">
      🎹 楽器体験フォームはこちら
    </a>
  </p>
</div>

  <script>
    let current = 0;
    let musicExperience = "";
    const questions = document.querySelectorAll('.question');
    const startScreen = document.getElementById('start-screen');
    const result = document.getElementById('result');
    const extraMessage = document.getElementById('extra-message');
    const twitterShare = document.getElementById('twitter-share');

    function startQuiz() {
      startScreen.classList.remove('active');
      questions[0].classList.add('active');
    }

    function nextQuestion() {
      if (current < questions.length - 1) {
        questions[current].classList.remove('active');
        current++;
        questions[current].classList.add('active');
      }
    }

    function showResult(answer = "") {
      if (answer) musicExperience = answer;

      questions[current].classList.remove('active');
      result.classList.add('active');

      let message = "";
      if (musicExperience === "yes") {
        message = "音楽経験があるあなたはさらに楽しめます！大学で新しいことに挑戦してみませんか？新しい音楽仲間と一緒に奏でよう♪";
      } else {
        message = "音楽経験がなくても、安心して上達できるマンドリンオーケストラ部がおすすめ！";
      }
      extraMessage.textContent = message;

      // Twitterシェア用リンク生成
      const shareText = encodeURIComponent("＼診断結果🎶／\nあなたにぴったりの部活は…マンドリンオーケストラ部！\n" + message + "\n#京女生診断");
      twitterShare.href = `https://twitter.com/intent/tweet?text=${shareText}`;
    }
  </script>
</body>
</html>
