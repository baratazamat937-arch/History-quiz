<!DOCTYPE html>
<html lang="kk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🇰🇿 Қазақстан Тарихы — Тест</title>
<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Georgia', serif;
  }

  body {
    min-height: 100vh;
    background: linear-gradient(135deg, #2b1810 0%, #4a2818 50%, #2b1810 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
    position: relative;
    overflow-x: hidden;
  }

  /* Фон ornament pattern */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: 
      radial-gradient(circle at 20% 30%, rgba(212,175,55,0.08) 0%, transparent 40%),
      radial-gradient(circle at 80% 70%, rgba(212,175,55,0.08) 0%, transparent 40%);
    pointer-events: none;
  }

  .container {
    width: 100%;
    max-width: 700px;
    background: linear-gradient(145deg, #3a2218, #2a1810);
    border: 2px solid #d4af37;
    border-radius: 20px;
    padding: 40px 35px;
    box-shadow: 
      0 0 40px rgba(212,175,55,0.3),
      0 20px 60px rgba(0,0,0,0.6),
      inset 0 1px 0 rgba(255,255,255,0.1);
    position: relative;
    z-index: 1;
    animation: fadeIn 0.6s ease-out;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(30px) scale(0.95); }
    to { opacity: 1; transform: translateY(0) scale(1); }
  }

  /* Декоративті бұрыштар */
  .container::before,
  .container::after {
    content: '❖';
    position: absolute;
    color: #d4af37;
    font-size: 20px;
    opacity: 0.7;
  }
  .container::before { top: 10px; left: 15px; }
  .container::after { bottom: 10px; right: 15px; }

  /* ===== HEADER ===== */
  .header {
    text-align: center;
    margin-bottom: 30px;
    padding-bottom: 20px;
    border-bottom: 2px solid rgba(212,175,55,0.3);
  }

  .header h1 {
    font-size: 26px;
    color: #d4af37;
    letter-spacing: 2px;
    margin-bottom: 8px;
    text-shadow: 0 2px 10px rgba(212,175,55,0.4);
    font-weight: 700;
  }

  .header p {
    color: #c9a86a;
    font-size: 13px;
    font-style: italic;
    letter-spacing: 1px;
  }

  /* ===== PROGRESS ===== */
  .progress-wrap {
    margin-bottom: 25px;
  }

  .progress-info {
    display: flex;
    justify-content: space-between;
    color: #d4af37;
    font-size: 13px;
    margin-bottom: 8px;
    font-weight: 600;
    letter-spacing: 0.5px;
  }

  .progress-bar {
    width: 100%;
    height: 8px;
    background: rgba(0,0,0,0.5);
    border-radius: 4px;
    overflow: hidden;
    border: 1px solid rgba(212,175,55,0.3);
  }

  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #d4af37, #f5d76e);
    width: 0%;
    transition: width 0.5s ease;
    box-shadow: 0 0 10px #d4af37;
  }

  /* ===== QUESTION ===== */
  .question-box {
    animation: slideIn 0.4s ease-out;
  }

  @keyframes slideIn {
    from { opacity: 0; transform: translateX(20px); }
    to { opacity: 1; transform: translateX(0); }
  }

  .question-text {
    color: #f5e6c8;
    font-size: 18px;
    line-height: 1.5;
    margin-bottom: 25px;
    padding: 15px;
    background: rgba(0,0,0,0.3);
    border-left: 4px solid #d4af37;
    border-radius: 8px;
    font-weight: 500;
  }

  /* ===== ANSWERS ===== */
  .answers {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .answer-btn {
    padding: 16px 20px;
    background: linear-gradient(145deg, #4a2c1e, #3a2015);
    border: 2px solid rgba(212,175,55,0.4);
    border-radius: 12px;
    color: #f5e6c8;
    font-size: 15px;
    font-family: 'Georgia', serif;
    text-align: left;
    cursor: pointer;
    transition: all 0.3s ease;
    position: relative;
    display: flex;
    align-items: center;
    gap: 12px;
    font-weight: 500;
  }

  .answer-btn::before {
    content: attr(data-letter);
    display: flex;
    align-items: center;
    justify-content: center;
    width: 32px;
    height: 32px;
    background: rgba(212,175,55,0.15);
    border: 1.5px solid #d4af37;
    border-radius: 50%;
    color: #d4af37;
    font-weight: 700;
    font-size: 14px;
    flex-shrink: 0;
    transition: all 0.3s ease;
  }

  .answer-btn:hover:not(:disabled) {
    background: linear-gradient(145deg, #5a3624, #4a2c1e);
    border-color: #d4af37;
    transform: translateX(5px);
    box-shadow: 0 5px 20px rgba(212,175,55,0.3);
  }

  .answer-btn:hover:not(:disabled)::before {
    background: #d4af37;
    color: #2b1810;
  }

  .answer-btn:disabled {
    cursor: not-allowed;
  }

  .answer-btn.correct {
    background: linear-gradient(145deg, #1e5a2e, #144020);
    border-color: #4ade80;
    animation: pulseCorrect 0.5s ease;
  }

  .answer-btn.correct::before {
    background: #4ade80;
    border-color: #4ade80;
    color: #fff;
    content: '✓';
  }

  .answer-btn.wrong {
    background: linear-gradient(145deg, #5a1e1e, #401414);
    border-color: #f87171;
    animation: shake 0.5s ease;
  }

  .answer-btn.wrong::before {
    background: #f87171;
    border-color: #f87171;
    color: #fff;
    content: '✕';
  }

  @keyframes pulseCorrect {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.03); box-shadow: 0 0 30px rgba(74,222,128,0.6); }
  }

  @keyframes shake {
    0%, 100% { transform: translateX(0); }
    25% { transform: translateX(-8px); }
    75% { transform: translateX(8px); }
  }

  /* ===== NEXT BUTTON ===== */
  .next-btn {
    margin-top: 20px;
    width: 100%;
    padding: 15px;
    background: linear-gradient(145deg, #d4af37, #b8942a);
    border: none;
    border-radius: 12px;
    color: #2b1810;
    font-size: 16px;
    font-weight: 700;
    font-family: 'Georgia', serif;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all 0.3s ease;
    display: none;
    box-shadow: 0 5px 15px rgba(212,175,55,0.4);
  }

  .next-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(212,175,55,0.6);
  }

  /* ===== RESULT ===== */
  .result {
    text-align: center;
    animation: fadeIn 0.6s ease;
  }

  .result-icon {
    font-size: 80px;
    margin-bottom: 15px;
    animation: bounceIn 0.8s ease;
  }

  @keyframes bounceIn {
    0% { transform: scale(0); }
    50% { transform: scale(1.2); }
    100% { transform: scale(1); }
  }

  .result h2 {
    color: #d4af37;
    font-size: 28px;
    margin-bottom: 15px;
    letter-spacing: 1px;
  }

  .result-score {
    font-size: 50px;
    color: #f5d76e;
    font-weight: 700;
    margin: 20px 0;
    text-shadow: 0 0 20px rgba(245,215,110,0.5);
  }

  .result-score span {
    font-size: 24px;
    color: #c9a86a;
  }

  .result-grade {
    display: inline-block;
    padding: 10px 30px;
    background: linear-gradient(145deg, #4a2c1e, #3a2015);
    border: 2px solid #d4af37;
    border-radius: 50px;
    color: #d4af37;
    font-size: 22px;
    font-weight: 700;
    margin: 15px 0 25px;
    letter-spacing: 2px;
  }

  .result-message {
    color: #c9a86a;
    font-size: 15px;
    font-style: italic;
    margin-bottom: 25px;
    line-height: 1.6;
  }

  .restart-btn {
    padding: 15px 40px;
    background: linear-gradient(145deg, #d4af37, #b8942a);
    border: none;
    border-radius: 12px;
    color: #2b1810;
    font-size: 15px;
    font-weight: 700;
    font-family: 'Georgia', serif;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 5px 15px rgba(212,175,55,0.4);
  }

  .restart-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(212,175,55,0.6);
  }

  /* ===== MOBILE ===== */
  @media (max-width: 500px) {
    .container { padding: 25px 20px; }
    .header h1 { font-size: 20px; }
    .question-text { font-size: 16px; }
    .answer-btn { font-size: 14px; padding: 14px 15px; }
    .result-score { font-size: 40px; }
  }
</style>
</head>
<body>

<div class="container">
  <div class="header">
    <h1>❖ ҚАЗАҚСТАН ТАРИХЫ ❖</h1>
    <p>Біліміңді сынап көр</p>
  </div>

  <div class="progress-wrap">
    <div class="progress-info">
      <span id="progress-text">Сұрақ 1 / 10</span>
      <span id="score-text">Ұпай: 0</span>
    </div>
    <div class="progress-bar">
      <div class="progress-fill" id="progress-fill"></div>
    </div>
  </div>

  <div id="content"></div>
</div>

<script>
// ============ СҰРАҚТАР ============
const questions = [
  {
    q: "Қазақ хандығы қай жылы құрылды?",
    answers: ["1465 жылы", "1365 жылы", "1565 жылы", "1265 жылы"],
    correct: 0
  },
  {
    q: "Қазақ хандығының негізін салушылар кімдер?",
    answers: ["Абылай мен Әбілқайыр", "Керей мен Жәнібек", "Тәуке мен Есім", "Қасым мен Хақназар"],
    correct: 1
  },
  {
    q: "Сақтардың атақты патшайымы кім?",
    answers: ["Зейнеп", "Томирис", "Сара", "Айша"],
    correct: 1
  },
  {
    q: "Түрік қағанаты қай жылы құрылды?",
    answers: ["452 жылы", "552 жылы", "652 жылы", "752 жылы"],
    correct: 1
  },
  {
    q: "Абылай хан қай ғасырда өмір сүрді?",
    answers: ["XVI ғасыр", "XVII ғасыр", "XVIII ғасыр", "XIX ғасыр"],
    correct: 2
  },
  {
    q: "Қазақстан тәуелсіздігін қай жылы жариялады?",
    answers: ["1989 жылы", "1990 жылы", "1991 жылы", "1992 жылы"],
    correct: 2
  },
  {
    q: "Алтын Орда қай жылы құрылды?",
    answers: ["1143 жылы", "1243 жылы", "1343 жылы", "1443 жылы"],
    correct: 1
  },
  {
    q: "Алаш Орда үкіметі қай жылы құрылды?",
    answers: ["1905 жылы", "1917 жылы", "1920 жылы", "1925 жылы"],
    correct: 1
  },
  {
    q: "Кенесары Қасымов көтерілісі қай жылдары болды?",
    answers: ["1825-1835", "1837-1847", "1850-1860", "1865-1875"],
    correct: 1
  },
  {
    q: "Қазақстанның тұңғыш Президенті кім?",
    answers: ["Қасым-Жомарт Тоқаев", "Нұрсұлтан Назарбаев", "Дінмұхамед Қонаев", "Олжас Сүлейменов"],
    correct: 1
  }
];

// ============ STATE ============
let currentQ = 0;
let score = 0;
let answered = false;

// ============ ELEMENTS ============
const content = document.getElementById('content');
const progressText = document.getElementById('progress-text');
const scoreText = document.getElementById('score-text');
const progressFill = document.getElementById('progress-fill');

const letters = ['A', 'B', 'C', 'D'];

// ============ RENDER QUESTION ============
function renderQuestion() {
  answered = false;
  const q = questions[currentQ];

  content.innerHTML = `
    <div class="question-box">
      <div class="question-text">${q.q}</div>
      <div class="answers">
        ${q.answers.map((a, i) => `
          <button class="answer-btn" data-index="${i}" data-letter="${letters[i]}">
            ${a}
          </button>
        `).join('')}
      </div>
      <button class="next-btn" id="nextBtn">
        ${currentQ === questions.length - 1 ? '🏆 НӘТИЖЕНІ КӨРУ' : 'КЕЛЕСІ СҰРАҚ →'}
      </button>
    </div>
  `;

  // Answer listeners
  document.querySelectorAll('.answer-btn').forEach(btn => {
    btn.addEventListener('click', () => handleAnswer(parseInt(btn.dataset.index), btn));
  });

  document.getElementById('nextBtn').addEventListener('click', nextQuestion);

  updateProgress();
}

// ============ HANDLE ANSWER ============
function handleAnswer(index, btn) {
  if (answered) return;
  answered = true;

  const q = questions[currentQ];
  const buttons = document.querySelectorAll('.answer-btn');

  buttons.forEach(b => b.disabled = true);

  if (index === q.correct) {
    btn.classList.add('correct');
    score++;
    scoreText.textContent = `Ұпай: ${score}`;
  } else {
    btn.classList.add('wrong');
    buttons[q.correct].classList.add('correct');
  }

  document.getElementById('nextBtn').style.display = 'block';
}

// ============ NEXT ============
function nextQuestion() {
  currentQ++;
  if (currentQ < questions.length) {
    renderQuestion();
  } else {
    renderResult();
  }
}

// ============ PROGRESS ============
function updateProgress() {
  progressText.textContent = `Сұрақ ${currentQ + 1} / ${questions.length}`;
  progressFill.style.width = `${((currentQ) / questions.length) * 100}%`;
}

// ============ RESULT ============
function renderResult() {
  progressFill.style.width = '100%';
  progressText.textContent = `Аяқталды!`;
  scoreText.textContent = `Ұпай: ${score}`;

  const percent = (score / questions.length) * 100;
  let grade, icon, msg;

  if (percent === 100) {
    grade = 'A+'; icon = '🏆';
    msg = 'Керемет! Сен нағыз тарих білгірісің! 🇰🇿';
  } else if (percent >= 80) {
    grade = 'A'; icon = '⭐';
    msg = 'Тамаша нәтиже! Білімің мықты!';
  } else if (percent >= 60) {
    grade = 'B'; icon = '👍';
    msg = 'Жақсы! Тағы да жаттықсаң, тамаша болады!';
  } else if (percent >= 40) {
    grade = 'C'; icon = '📚';
    msg = 'Орташа. Тарихты оқып, қайта көр!';
  } else {
    grade = 'D'; icon = '💪';
    msg = 'Бастау — әрқашан қиын. Оқып, қайталап көр!';
  }

  content.innerHTML = `
    <div class="result">
      <div class="result-icon">${icon}</div>
      <h2>ТЕСТ АЯҚТАЛДЫ</h2>
      <div class="result-score">
        ${score}<span> / ${questions.length}</span>
      </div>
      <div class="result-grade">${grade}</div>
      <div class="result-message">${msg}</div>
      <button class="restart-btn" id="restartBtn">🔄 ҚАЙТА БАСТАУ</button>
    </div>
  `;

  document.getElementById('restartBtn').addEventListener('click', restart);
}

// ============ RESTART ============
function restart() {
  currentQ = 0;
  score = 0;
  answered = false;
  scoreText.textContent = `Ұпай: 0`;
  progressFill.style.width = '0%';
  renderQuestion();
}

// ============ START ============
renderQuestion();
</script>
</body>
</html>
