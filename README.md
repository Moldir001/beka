<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Валентинка для Беки</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');
        body {
            font-family: 'Pacifico', cursive;
            background-color: #ffe6e6;
            text-align: center;
            padding: 20px;
            position: relative;
            overflow: hidden;
        }
        .question {
            font-size: 26px;
            color: #d63384;
            margin-top: 50px;
        }
        .buttons {
            margin-top: 20px;
            position: relative;
        }
        button {
            font-size: 20px;
            padding: 10px 20px;
            margin: 10px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: 0.3s;
        }
        .yes {
            background-color: #ff4d79;
            color: white;
        }
        .no {
            background-color: #cccccc;
            color: black;
            position: absolute;
        }
        .hidden {
            display: none;
        }
        .valentine {
            font-size: 30px;
            color: #d63384;
            margin-top: 20px;
        }
        .cat-image {
            width: 300px;
            margin-top: 20px;
            border-radius: 15px;
        }
        .flashing-heart {
            font-size: 50px;
            color: red;
            animation: flash 1s infinite alternate;
            margin-top: 20px;
        }
        @keyframes flash {
            from { opacity: 1; }
            to { opacity: 0.3; }
        }
        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            clip-path: polygon(50% 0%, 100% 35%, 80% 100%, 50% 80%, 20% 100%, 0% 35%);
            animation: fall linear infinite;
        }
        @keyframes fall {
            from {
                transform: translateY(-10vh);
                opacity: 1;
            }
            to {
                transform: translateY(100vh);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <div id="question-container">
        <p class="question">Бека, ты меня любишь? ❤️</p>
        <div class="buttons">
            <button class="yes" onclick="showValentine()">Да</button>
            <button class="no" id="no-btn" onmouseover="moveButton()">Нет</button>
        </div>
    </div>
    
    <div id="valentine" class="hidden">
        <h1>Я люблю тебя,жанм
             ❤️</h1>
        <p class="valentine">Ты – самое дорогое, что у меня есть!</p>
        <p class="valentine">Ты мое счастье, моя радость, мой смысл жизни! 💕</p>
        <img src="котик.jpeg" alt="Милый котик" class="cat-image">
        <p class="flashing-heart">❤️❤️❤️</p>
    </div>
    
    <script>
        function showValentine() {
            document.getElementById('question-container').classList.add('hidden');
            document.getElementById('valentine').classList.remove('hidden');
        }
        
        function moveButton() {
            let btn = document.getElementById('no-btn');
            let x = Math.random() * (window.innerWidth - btn.offsetWidth);
            let y = Math.random() * (window.innerHeight - btn.offsetHeight);
            btn.style.left = `${x}px`;
            btn.style.top = `${y}px`;
        }
        
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 3 + 2 + 's';
            document.body.appendChild(heart);
            setTimeout(() => {
                heart.remove();
            }, 5000);
        }
        setInterval(createHeart, 300);
    </script>
</body>
</html>
