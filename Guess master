<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>AI Mind Reader | ИИ Угадай Число</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #0a0f2a, #030617);
            font-family: 'Segoe UI', 'Poppins', system-ui, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .game-container {
            max-width: 550px;
            width: 100%;
            background: rgba(10, 20, 40, 0.7);
            backdrop-filter: blur(16px);
            border-radius: 64px;
            border: 1px solid rgba(0, 255, 255, 0.4);
            box-shadow: 0 20px 40px rgba(0,0,0,0.5), 0 0 20px rgba(0,200,255,0.2);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(145deg, #0b1428, #01050f);
            padding: 28px 20px 20px;
            text-align: center;
            border-bottom: 2px solid #0ff;
        }

        .header h1 {
            font-size: 32px;
            background: linear-gradient(45deg, #fff, #0ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 2px;
        }

        .sub {
            color: #8ab3cf;
            margin-top: 8px;
            font-size: 14px;
        }

        .difficulty {
            display: flex;
            gap: 12px;
            padding: 20px;
            justify-content: center;
            flex-wrap: wrap;
            background: #030b14;
        }

        .diff-btn {
            background: #121e2c;
            border: none;
            padding: 10px 24px;
            border-radius: 60px;
            color: #bbf0ff;
            font-weight: bold;
            font-size: 18px;
            cursor: pointer;
            transition: 0.2s;
            box-shadow: 0 2px 6px black;
        }

        .diff-btn.active {
            background: #0ff;
            color: #010514;
            box-shadow: 0 0 12px cyan;
            border: 1px solid white;
        }

        .game-area {
            padding: 20px 25px 30px;
        }

        .info-panel {
            background: #07121e80;
            border-radius: 48px;
            padding: 18px;
            text-align: center;
            margin-bottom: 25px;
            border: 1px solid #2c5770;
        }

        .range-text {
            font-size: 20px;
            color: #88ddff;
        }

        .ai-guess {
            font-size: 64px;
            font-weight: bold;
            background: linear-gradient(135deg, #fff, #0ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin: 15px 0;
            letter-spacing: 4px;
        }

        .attempts {
            font-size: 18px;
            color: #ffd966;
        }

        .control-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
            margin: 25px 0 20px;
        }

        .game-btn {
            background: #101c2c;
            border: 1px solid #2f6f8a;
            padding: 14px 8px;
            border-radius: 60px;
            font-size: 20px;
            font-weight: bold;
            color: #caf0ff;
            cursor: pointer;
            transition: 0.15s;
        }

        .game-btn:active {
            transform: scale(0.96);
        }

        .correct-btn {
            background: #0a5c3e;
            border-color: #0f0;
            color: white;
            box-shadow: 0 0 8px #0f0;
        }

        .reset-btn {
            background: #4a1e2c;
            border-color: #ff7777;
            color: #ffaaaa;
        }

        .message-box {
            background: #000000aa;
            border-radius: 40px;
            padding: 14px;
            text-align: center;
            color: #bbe1ff;
            font-size: 16px;
            margin-top: 15px;
            border-left: 6px solid cyan;
        }

        @keyframes pulse {
            0% { text-shadow: 0 0 0 cyan; opacity: 0.7;}
            100% { text-shadow: 0 0 12px cyan; opacity: 1;}
        }

        .animate-guess {
            animation: pulse 0.25s ease-in-out;
        }

        footer {
            text-align: center;
            padding: 20px;
            color: #6c8eb0;
            font-size: 12px;
            border-top: 1px solid rgba(0,255,255,0.2);
            background: #030b14;
        }
    </style>
</head>
<body>
    <div class="game-container">
        <div class="header">
            <h1>🤖 AI УГАДАЙ ЧИСЛО</h1>
            <div class="sub">Загадай число, искусственный интеллект отгадает</div>
        </div>

        <div class="difficulty">
            <button class="diff-btn" data-max="10">🔹 1–10</button>
            <button class="diff-btn active" data-max="100">🔸 1–100</button>
            <button class="diff-btn" data-max="1000">🔺 1–1000</button>
            <button class="diff-btn" data-max="10000">🔥 1–10000</button>
        </div>

        <div class="game-area">
            <div class="info-panel">
                <div class="range-text">📡 Диапазон: <span id="rangeDisplay">1 – 100</span></div>
                <div class="ai-guess" id="aiGuess">50</div>
                <div class="attempts">🧠 Попыток: <span id="attemptCount">0</span></div>
            </div>

            <div class="control-grid">
                <button class="game-btn" id="lowerBtn">⬇️ МЕНЬШЕ</button>
                <button class="game-btn" id="higherBtn">⬆️ БОЛЬШЕ</button>
                <button class="game-btn correct-btn" id="correctBtn">✅ ВЕРНО!</button>
                <button class="game-btn reset-btn" id="resetGameBtn">🔄 НОВАЯ ИГРА</button>
            </div>

            <div class="message-box" id="messageBox">
                💡 Загадай число от 1 до 100. Нажимай "Меньше" / "Больше" пока ИИ не угадает.
            </div>
        </div>
        <footer>
            <p>🧠 AI Mind Reader — игра с бинарным поиском | GitHub Pages</p>
        </footer>
    </div>

    <script>
        let minRange = 1;
        let maxRange = 100;
        let currentGuess = 50;
        let attempts = 0;
        let gameActive = true;
        let lastGuessCorrect = false;
        
        const rangeDisplay = document.getElementById('rangeDisplay');
        const aiGuessSpan = document.getElementById('aiGuess');
        const attemptSpan = document.getElementById('attemptCount');
        const messageBox = document.getElementById('messageBox');
        
        const lowerBtn = document.getElementById('lowerBtn');
        const higherBtn = document.getElementById('higherBtn');
        const correctBtn = document.getElementById('correctBtn');
        const resetBtn = document.getElementById('resetGameBtn');
        const diffBtns = document.querySelectorAll('.diff-btn');
        
        function updateAIGuess() {
            if (!gameActive) return;
            let newGuess = Math.floor((minRange + maxRange) / 2);
            currentGuess = newGuess;
            aiGuessSpan.innerText = currentGuess;
            aiGuessSpan.classList.add('animate-guess');
            setTimeout(() => aiGuessSpan.classList.remove('animate-guess'), 300);
            if (minRange > maxRange && gameActive) {
                messageBox.innerHTML = "❌ Ошибка! Диапазон пуст. Нажми «Новая игра».";
                gameActive = false;
                aiGuessSpan.innerText = "?!";
            }
        }
        
        function updateUI() {
            rangeDisplay.innerText = `${minRange} – ${maxRange}`;
            attemptSpan.innerText = attempts;
        }
        
        function handleLower() {
            if (!gameActive) {
                messageBox.innerHTML = "⚠️ Игра завершена. Нажми «Новая игра».";
                return;
            }
            if (currentGuess <= minRange) {
                messageBox.innerHTML = "🤔 Число не может быть меньше. Нажми «ВЕРНО» если угадал.";
                return;
            }
            maxRange = currentGuess - 1;
            attempts++;
            updateUI();
            if (minRange > maxRange) {
                messageBox.innerHTML = "🔴 ОШИБКА: диапазон пуст! Перезапусти игру.";
                gameActive = false;
                aiGuessSpan.innerText = "❌";
                return;
            }
            updateAIGuess();
            messageBox.innerHTML = `🎯 Диапазон сузился до ${minRange}–${maxRange}`;
        }
        
        function handleHigher() {
            if (!gameActive) {
                messageBox.innerHTML = "⚠️ Игра завершена. Нажми «Новая игра».";
                return;
            }
            if (currentGuess >= maxRange) {
                messageBox.innerHTML = "🤔 Число не может быть больше. Нажми «ВЕРНО» если угадал.";
                return;
            }
            minRange = currentGuess + 1;
            attempts++;
            updateUI();
            if (minRange > maxRange) {
                messageBox.innerHTML = "🔴 ОШИБКА: диапазон пуст! Перезапусти игру.";
                gameActive = false;
                aiGuessSpan.innerText = "❌";
                return;
            }
            updateAIGuess();
            messageBox.innerHTML = `🎯 Диапазон сузился до ${minRange}–${maxRange}`;
        }
        
        function handleCorrect() {
            if (!gameActive && lastGuessCorrect === false) {
                messageBox.innerHTML = "🎮 Нажми «Новая игра»";
                return;
            }
            if (!gameActive) {
                resetGame();
            }
            gameActive = false;
            lastGuessCorrect = true;
            messageBox.innerHTML = `🎉 ПОБЕДА! ИИ угадал число ${currentGuess} за ${attempts} попыток! 🎉`;
            aiGuessSpan.style.animation = 'pulse 0.5s ease';
            setTimeout(() => { aiGuessSpan.style.animation = ''; }, 500);
        }
        
        function resetGame() {
            let activeDiff = document.querySelector('.diff-btn.active');
            let maxVal = parseInt(activeDiff.getAttribute('data-max'));
            minRange = 1;
            maxRange = maxVal;
            attempts = 0;
            gameActive = true;
            lastGuessCorrect = false;
            currentGuess = Math.floor((minRange + maxRange) / 2);
            aiGuessSpan.innerText = currentGuess;
            updateUI();
            messageBox.innerHTML = `✨ Новая игра! Загадай число от 1 до ${maxVal}`;
            gameActive = true;
        }
        
        function setDifficulty(maxVal) {
            diffBtns.forEach(btn => {
                if (parseInt(btn.getAttribute('data-max')) === maxVal) {
                    btn.classList.add('active');
                } else {
                    btn.classList.remove('active');
                }
            });
            minRange = 1;
            maxRange = maxVal;
            attempts = 0;
            gameActive = true;
            lastGuessCorrect = false;
            currentGuess = Math.floor((minRange + maxRange) / 2);
            aiGuessSpan.innerText = currentGuess;
            updateUI();
            messageBox.innerHTML = `🧠 Диапазон ${minRange}–${maxRange}. Загадай число!`;
        }
        
        lowerBtn.addEventListener('click', handleLower);
        higherBtn.addEventListener('click', handleHigher);
        correctBtn.addEventListener('click', handleCorrect);
        resetBtn.addEventListener('click', resetGame);
        
        diffBtns.forEach(btn => {
            btn.addEventListener('click', (e) => {
                let maxVal = parseInt(btn.getAttribute('data-max'));
                setDifficulty(maxVal);
            });
        });
        
        setDifficulty(100);
    </script>
</body>
</html>
