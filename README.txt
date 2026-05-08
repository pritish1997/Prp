<!DOCTYPE html> 
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Special</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&display=swap" rel="stylesheet" />
    <style>
        body {
            font-family: 'Dancing Script', cursive;
            background: linear-gradient(135deg, #ffe6f2, #ffb3ba);
            color: #d63384;
            text-align: center;
            padding: 60px 20px;
            margin: 0;
            overflow-x: hidden;
            animation: fadeIn 2s ease forwards;
        }
        @keyframes fadeIn {
            from {opacity: 0;}
            to {opacity: 1;}
        }
        h1 {
            font-size: 3.5em;
            margin-bottom: 0.2em;
            text-shadow: 2px 2px 5px rgba(0,0,0,0.25);
            animation: pulse 2.5s infinite ease-in-out;
        }
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        p.lead {
            font-size: 1.3em;
            max-width: 600px;
            margin: 0 auto 30px auto;
            line-height: 1.5;
            font-weight: 600;
        }
        button {
            font-size: 1.6em;
            padding: 18px 45px;
            margin: 20px 15px 40px;
            border-radius: 50px;
            border: none;
            cursor: pointer;
            box-shadow: 0 6px 15px rgba(214,51,132,0.3);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        #yes {
            background: linear-gradient(45deg, #ff69b4, #ff1493);
            color: white;
            font-weight: 700;
        }
        #yes:hover {
            transform: scale(1.15);
            box-shadow: 0 10px 25px rgba(255,20,147,0.6);
        }
        #no {
            background: linear-gradient(45deg, #ccc, #999);
            color: #666;
            font-weight: 600;
            position: relative;
        }
        #no:hover {
            background: linear-gradient(45deg, #ff4500, #dc143c);
            color: white;
            transform: rotate(10deg);
        }
        #congrats {
            display: none;
            animation: slideInUp 1.2s ease forwards;
            max-width: 600px;
            margin: 0 auto;
            font-weight: 700;
        }
        @keyframes slideInUp {
            from {
                transform: translateY(100px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }
        .hearts {
            position: fixed;
            top: 0; left: 0;
            width: 100vw; height: 100vh;
            pointer-events: none;
            overflow: hidden;
            z-index: 0;
        }
        .heart {
            position: absolute;
            color: #ff69b4;
            font-size: 2.5em;
            animation: floatUp 6s linear infinite;
            user-select: none;
        }
        @keyframes floatUp {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }
        @media (max-width: 600px) {
            h1 {
                font-size: 2.2em;
            }
            p.lead {
                font-size: 1.1em;
            }
            button {
                font-size: 1.2em;
                padding: 14px 35px;
                margin: 15px 10px 35px;
            }
        }
    </style>
</head>
<body>
    <div class="hearts" id="hearts"></div>
    <div id="proposal">
        <h1>Hey Faith,<br> Do you love me</h1>  <img src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExcm9waHdtbnN2N3h3dWQ4ODUyZXJ5anh5bnJycWRkZWFlaTZzZ3pjeiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/kD62fyVdWl4UmtfLiA/giphy.gif" alt="Heart animation" width="150" style="border-radius: 20px; box-shadow: 0 6px 15px rgba(214,51,132,0.3);" />
        <p class="lead">With every beat of my heart, I hope this message finds you smiling🙂..<br><br>You know… I really enjoy being around you. Somehow, you make me smile even on ordinary days. I don’t know what the future holds, but I’d really like to be someone who makes you happy too. Let's create memories that bloom like roses and shine brighter than the stars ✨.</p>
        <button id="yes">Yes 💖</button>
        <button id="no">No 😢</button>
    </div>

    <div id="congrats">
        <h1>Congratulations & Thank You, Love! 💘</h1>
        <p class="lead">You've made my world a thousand times sweeter.Wow… you have no idea how happy you just made me! I promise to do my best to make you smile every day, share little moments, laugh together, and just be there for you. I can already tell this is going to be something really special, and I can’t wait to see that amazing smile of yours more often..</p>
        <img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXlzMDJ4eGJ0a2cxa242djA2am4wenQ0Z2tnbmV1ZmpueTR0bDNrMCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/jUiRE0e7vA4h6xhByZ/giphy.gif" alt="Heart animation" width="350" style="border-radius: 20px; box-shadow: 0 6px 15px rgba(214,51,132,0.3);" />
    </div>

    <script>
        const noBtn = document.getElementById('no');
        const yesBtn = document.getElementById('yes');
        const proposalDiv = document.getElementById('proposal');
        const congratsDiv = document.getElementById('congrats');
        const heartsContainer = document.getElementById('hearts');

        // Floating hearts effect
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.textContent = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDelay = Math.random() * 6 + 's';
            heart.style.fontSize = (15 + Math.random() * 20) + 'px';
            heartsContainer.appendChild(heart);
            setTimeout(() => heart.remove(), 6000);
        }
        setInterval(createHeart, 400);

        // No button avoids mouse hover with smooth random moves
        noBtn.addEventListener('mouseover', () => {
            const x = Math.random() * (window.innerWidth - 140);
            const y = Math.random() * (window.innerHeight - 140);
            noBtn.style.position = 'absolute';
            noBtn.style.left = `${x}px`;
            noBtn.style.top = `${y}px`;
        });

        // Yes button click: show congratulations
        yesBtn.addEventListener('click', () => {
            proposalDiv.style.display = 'none';
            congratsDiv.style.display = 'block';
        });
    </script>
</body>
</html>

