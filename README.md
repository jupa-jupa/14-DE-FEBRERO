<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Invitación a San Valentín</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ff6b9d 0%, #c73e5c 25%, #ffd93d 50%, #ff6b9d 75%, #c73e5c 100%);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            position: relative;
            overflow: hidden;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .floating-hearts {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            overflow: hidden;
        }

        .heart {
            position: absolute;
            font-size: 2rem;
            opacity: 0.6;
            animation: float 6s infinite ease-in-out;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.6;
            }
            90% {
                opacity: 0.6;
            }
            100% {
                transform: translateY(-100vh) rotate(360deg);
                opacity: 0;
            }
        }

        .container {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 30px;
            padding: 40px 30px;
            text-align: center;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            max-width: 600px;
            z-index: 10;
            position: relative;
            border: 3px solid #ff6b9d;
        }

        .top-image-container {
            margin-bottom: 20px;
            min-height: 150px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .top-image-container img {
            max-width: 100%;
            max-height: 200px;
            border-radius: 15px;
            box-shadow: 0 8px 20px rgba(255, 107, 157, 0.3);
        }

        h1 {
            color: #c73e5c;
            font-size: 2rem;
            margin-bottom: 30px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        .buttons-container {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
            margin-bottom: 30px;
            position: relative;
            min-height: 60px;
        }

        button {
            padding: 12px 30px;
            font-size: 1rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
        }

        #siBtn {
            background: linear-gradient(135deg, #2ecc71, #27ae60);
            color: white;
            position: relative;
            z-index: 5;
        }

        #siBtn:hover {
            transform: scale(1.1);
            box-shadow: 0 12px 25px rgba(46, 204, 113, 0.5);
        }

        #noBtn {
            background: linear-gradient(135deg, #e74c3c, #c0392b);
            color: white;
            position: relative;
        }

        #noBtn:hover {
            transform: translate(20px, -15px) scale(0.9);
        }

        #siBtn.giant {
            padding: 40px 100px;
            font-size: 2rem;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) !important;
            z-index: 100;
        }

        .success-message {
            margin-top: 20px;
            padding: 30px;
            background: linear-gradient(135deg, #ffd93d, #ffed4e);
            border-radius: 20px;
            border: 3px solid #c73e5c;
        }

        .success-message h2 {
            color: #c73e5c;
            margin-bottom: 20px;
            font-size: 2rem;
        }

        .custom-image-section {
            margin: 20px 0;
            padding: 20px;
            background: rgba(255, 200, 221, 0.3);
            border-radius: 15px;
            border: 2px dashed #ff6b9d;
        }

        .custom-image-section img {
            max-width: 100%;
            max-height: 300px;
            border-radius: 15px;
            margin: 10px 0;
            box-shadow: 0 8px 20px rgba(255, 107, 157, 0.3);
        }

        .custom-text-section {
            margin: 20px 0;
            padding: 20px;
            background: rgba(255, 217, 61, 0.2);
            border-radius: 15px;
            border: 2px dashed #ffd93d;
        }

        .custom-text-section p {
            color: #333;
            font-size: 1rem;
            line-height: 1.6;
        }

        @keyframes confetti-fall {
            to {
                transform: translateY(100vh) rotateZ(360deg);
                opacity: 0;
            }
        }

        .confetti {
            position: fixed;
            pointer-events: none;
            opacity: 1;
        }

        @keyframes buttonShake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            75% { transform: translateX(10px); }
        }

        #noBtn.shake {
            animation: buttonShake 0.3s;
        }

        .hidden {
            display: none !important;
        }
    </style>
</head>
<body>
    <div class="floating-hearts" id="floatingHearts"></div>

    <div class="container">
        <!-- 🖼️ IMAGEN PRINCIPAL - REEMPLAZA AQUÍ -->
        <div class="top-image-container">
            <img src="https://i.pinimg.com/736x/8c/db/71/8cdb710e2e34fccca8481df939c9e061.jpg" alt="Imagen    Principal" id="topImg">
        </div>

        <h1 id="question">¿Quieres ser mi San Valentín?</h1>

        <div class="buttons-container">
            <button id="siBtn">💚 Sí</button>
            <button id="noBtn">No</button>
        </div>

        <div id="successContainer" class="hidden">
            <div class="success-message">
                <h2>¡Sabia que no te podias resistir! 💕</h2>
                
                <!-- 🖼️ IMAGEN ESPECIAL - REEMPLAZA AQUÍ -->
                <div class="custom-image-section">
                    <p style="color: #c73e5c; font-weight: bold; margin-bottom: 10px;"></p>
                    <img src="https://i.pinimg.com/736x/a7/99/bd/a799bd7183fa8097f2de8ec79fda17c6.jpg" alt="Imagen Especial" id="specialImg">
                </div>

                <div class="custom-text-section">
                    <p style="color: #c73e5c; font-weight: bold; margin-bottom: 10px;">TE ADOROOOOOO PRINCESA💌​💌​💌​</p>
                    <p id="specialMessage">
                        Te adoro con toda mi alma, que cada dia que pase sea junto a tí.
                    </p>
                </div>
            </div>
        </div>
    </div>

    <script>
        let noClickCount = 0;
        const maxNoClicks = 50;
        const siBtn = document.getElementById('siBtn');
        const noBtn = document.getElementById('noBtn');
        const question = document.getElementById('question');
        const successContainer = document.getElementById('successContainer');
        const buttonsContainer = document.querySelector('.buttons-container');
        const topImageContainer = document.querySelector('.top-image-container');

        const noMessages = [
            "No", "¿Segura?", "Piénsalo bien", "¿No me quieres?", "¿Ya no me amas :(?",
            "Tienes a otro, verdad", "Di que sí", "No seas mala", "Anda, sí", "¿Encerio?",
            "¿Pero segura?", "¿Super hyper mega segura?", "No te veo convencida", "Tan facil que es darle al si", "¿Le temes al exito?",
            "Es mejor que le des al si", "Por qué no??", "?", "??", "???",
            "Dimelo", "Dilo ya", "Que ya no me amas", "Tite", "Muy tite",
            "Tistisimo", "Voy a llorar", "Lloro enserio", "Pipipipipipi", "Conste",
            "Conste", "Yo te amo mucho", "¿Por qué sigues diciendo no?", "Hacemos una", "Pijamada real",
            "¿SIII?", "Pofiiis", "¡Di que sí!",
            "La magia existe", "Cree en nosotros", "Juntos somos fuertes", "Mi sueño eres tú", "¡Por favor!",
            "❤️", "💕", "💖", "Te amo", "¡SIIIIII! 😭💔"
        ];

        function createFloatingHearts() {
            const floatingHeartsContainer = document.getElementById('floatingHearts');
            const hearts = ['❤️', '💕', '💖', '💗', '💝', '😍','💜','💌','ღ','💟','💓', '🌻', '💐', '🌷',];
            
            for (let i = 0; i < 15; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
                heart.style.left = Math.random() * 100 + '%';
                heart.style.animationDelay = Math.random() * 2 + 's';
                heart.style.animationDuration = (Math.random() * 3 + 5) + 's';
                floatingHeartsContainer.appendChild(heart);
            }
        }

        function createConfetti() {
            const confettiPieces = 50;
            const colors = ['#2ecc71', '#ffd93d', '#c73e5c', '#27ae60', '#ffed4e'];
            
            for (let i = 0; i < confettiPieces; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.left = Math.random() * 100 + '%';
                confetti.style.top = '-10px';
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.width = Math.random() * 10 + 5 + 'px';
                confetti.style.height = confetti.style.width;
                confetti.style.borderRadius = '50%';
                confetti.style.animation = `confetti-fall ${Math.random() * 2 + 2}s ease-in forwards`;
                confetti.style.animationDelay = Math.random() * 0.3 + 's';
                
                document.body.appendChild(confetti);
                
                setTimeout(() => confetti.remove(), 3000);
            }
        }

        siBtn.addEventListener('click', function() {
            createConfetti();
            
            question.classList.add('hidden');
            topImageContainer.classList.add('hidden');
            buttonsContainer.classList.add('hidden');
            successContainer.classList.remove('hidden');
            
            document.body.style.animation = 'none';
            document.body.style.background = 'linear-gradient(135deg, #2ecc71 0%, #27ae60 25%, #ffd93d 50%, #27ae60 75%, #2ecc71 100%)';
        });

        noBtn.addEventListener('click', function() {
            noClickCount++;
            
            if (noClickCount <= maxNoClicks) {
                noBtn.textContent = noMessages[Math.min(noClickCount - 1, noMessages.length - 1)];
            }
            
            noBtn.classList.remove('shake');
            void noBtn.offsetWidth;
            noBtn.classList.add('shake');
            
            const increaseAmount = (noClickCount / maxNoClicks) * 100;
            const newScale = 1 + (increaseAmount / 100) * 1.5;
            siBtn.style.transform = `scale(${newScale})`;
            siBtn.style.padding = `${12 + (increaseAmount / 4)}px ${30 + (increaseAmount / 1.5)}px`;
            siBtn.style.fontSize = `${1 + (increaseAmount / 200)}rem`;
            siBtn.style.boxShadow = `0 ${10 + (increaseAmount / 5)}px ${30 + (increaseAmount / 2)}px rgba(46, 204, 113, ${0.4 + (increaseAmount / 250)})`;
            
            const decreaseAmount = (noClickCount / maxNoClicks) * 0.6;
            noBtn.style.transform = `scale(${Math.max(0.3, 1 - decreaseAmount)})`;
            noBtn.style.opacity = Math.max(0.2, 1 - (decreaseAmount / 2));
            
            const randomX = (Math.random() - 0.5) * 80;
            const randomY = (Math.random() - 0.5) * 80;
            noBtn.style.marginLeft = randomX + 'px';
            noBtn.style.marginTop = randomY + 'px';
            
            if (noClickCount >= maxNoClicks) {
                siBtn.classList.add('giant');
                noBtn.disabled = true;
                noBtn.style.opacity = '0.05';
                noBtn.style.cursor = 'not-allowed';
                noBtn.style.pointerEvents = 'none';
                
                createConfetti();
                
                question.textContent = '¡Esooooooooooo, sabía que no te podias resistir! ❤️​❤️​❤️​❤️​❤️​';
                question.classList.remove('hidden');
                setTimeout(() => {
                    question.classList.add('hidden');
                }, 3000);
            }
        });

        createFloatingHearts();
    </script>
</body>
</html>
