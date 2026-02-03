            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
        }
        #response {
            display: none;
            font-size: 2.5em;
            margin-top: 20px;
            animation: party 1s infinite;
        }
        @keyframes party {
            0%, 100% { transform: rotate(0deg) scale(1); }
            25% { transform: rotate(5deg) scale(1.1); }
            50% { transform: rotate(-5deg) scale(1.2); }
            75% { transform: rotate(5deg) scale(1.1); }
        }
        .heart {
            position: absolute;
            font-size: 2em;
            color: #ff1493;
            animation: floatAndSpin 4s linear infinite;
        }
        @keyframes floatAndSpin {
            0% { transform: translateY(100vh) rotate(0deg) scale(1); opacity: 1; }
            50% { transform: translateY(50vh) rotate(180deg) scale(1.5); }
            100% { transform: translateY(-100px) rotate(360deg) scale(0.5); opacity: 0; }
        }
        .confetti {
            position: absolute;
            width: 15px;
            height: 15px;
            background-color: #ffd700;
            border-radius: 50%;
            animation: fallAndTwist 3s linear infinite;
        }
        @keyframes fallAndTwist {
            0% { transform: translateY(-10px) rotate(0deg); opacity: 1; }
            100% { transform: translateY(100vh) rotate(720deg); opacity: 0; }
        }
        .firework {
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: #ff4500;
            border-radius: 50%;
            animation: explode 2s ease-out infinite;
        }
        @keyframes explode {
            0% { transform: scale(0); opacity: 1; }
            50% { transform: scale(2); opacity: 0.8; }
            100% { transform: scale(0); opacity: 0; }
        }
        .funnyText {
            position: absolute;
            font-size: 1.2em;
            color: #ff6347;
            animation: fadeInOut 2s ease-in-out infinite;
        }
        @keyframes fadeInOut {
            0%, 100% { opacity: 0; transform: translateY(0); }
            50% { opacity: 1; transform: translateY(-20px); }
        }
    </style>
</head>
<body>
    <h1>Can you be my Valentine? 💕😜</h1>
    <button id="yesBtn">Yes! 😍</button>
    <button id="noBtn">No 😏</button>
    <div id="response">I very happyyy you are my valentine now! 🎉❤️😍🥰🎊</div>

    <script>
        let yesScale = 1;
        const noTexts = [
            "Why not? 😢", 
            "Try again? 🥺", 
            "Please say yes! 🙏", 
            "Come on, click yes! 😂", 
            "Are you sure? 🤔", 
            "I'll cry! 😭", 
            "One more try? 😅", 
            "You're breaking my heart! 💔"
        ]; // More funny, varied texts
        let noClickCount = 0;

        document.getElementById('noBtn').addEventListener('click', function() {
            // Change No button text to something funny
            this.textContent = noTexts[noClickCount % noTexts.length];
            noClickCount++;

            // Make Yes button bigger and add a glow
            yesScale += 0.3;
            document.getElementById('yesBtn').style.transform = `scale(${yesScale})`;
            document.getElementById('yesBtn').style.boxShadow = `0 0 ${yesScale * 10}px #ff69b4`;

            // Funny animation: Make No button "run away" briefly
            this.style.animation = 'shake 0.5s';
            setTimeout(() => this.style.animation = '', 500);

            // Add a funny floating text near No button
            const funnyText = document.createElement('div');
            funnyText.className = 'funnyText';
            funnyText.textContent = 'Nope! 😜';
            funnyText.style.left = Math.random() * 50 + 25 + '%';
            funnyText.style.top = Math.random() * 50 + 25 + '%';
            document.body.appendChild(funnyText);
            setTimeout(() => funnyText.remove(), 2000);
        });

        document.getElementById('yesBtn').addEventListener('click', function() {
            // Hide buttons and show happy response
            document.getElementById('yesBtn').style.display = 'none';
            document.getElementById('noBtn').style.display = 'none';
            document.getElementById('response').style.display = 'block';

            // Add more floating hearts (doubled for fun)
            for (let i = 0; i < 20; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.textContent = '❤️';
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.animationDelay = Math.random() * 2 + 's';
                document.body.appendChild(heart);
                setTimeout(() => heart.remove(), 4000);
            }

            // Add more confetti (doubled and colorful)
            const colors = ['#ffd700', '#ff69b4', '#00ff00', '#ff4500', '#1e90ff'];
            for (let i = 0; i < 40; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.animationDelay = Math.random() * 2 + 's';
                document.body.appendChild(confetti);
                setTimeout(() => confetti.remove(), 3000);
            }

            // Add fireworks for extra fun
            for (let i = 0; i < 15; i++) {
                const firework = document.createElement('div');
                firework.className = 'firework';
                firework.style.left = Math.random() * 100 + 'vw';
                firework.style.top = Math.random() * 50 + 'vh';
                firework.style.animationDelay = Math.random() * 1 + 's';
                document.body.appendChild(firework);
                setTimeout(() => firework.remove(), 2000);
            }
        });
    </script>
</body>
</html>
