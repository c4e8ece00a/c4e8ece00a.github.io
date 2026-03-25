<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Наша любовь: С 2004 года</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Marck+Script&family=Montserrat:wght@300;400;700&display=swap');
        
        * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
        
        body {
            background: #0f0e17;
            color: white;
            font-family: 'Montserrat', sans-serif;
            margin: 0;
            height: 100vh;
            overflow: hidden;
        }

        .game-container {
            width: 100%;
            height: 100%;
            position: relative;
        }

        .scene-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            transition: opacity 1s ease-in-out;
            z-index: 1;
            background-color: #1a1a2e;
        }

        /* Цвета-заглушки на случай отсутствия картинок */
        .bg-2004-school { background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1580582932707-520aed937b7b?q=80&w=1200'); }
        .bg-school-walk { background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1525920980995-f8a382bf42c5?q=80&w=1200'); }
        .bg-separate-cities { background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1444723121867-7a241cacace9?q=80&w=1200'); }
        .bg-social-like { background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1516321318423-f06f85e504b3?q=80&w=1200'); }
        .bg-cafe-meet { background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?q=80&w=1200'); }
        .bg-dating { background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1515934751635-c81c6bc9a2d8?q=80&w=1200'); }
        .bg-wedding { background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'); }
        .bg-wedding-ring { background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1511795409834-ef04bbd61622?q=80&w=1200'); }

        .overlay {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(to bottom, transparent 20%, rgba(0,0,0,0.9) 90%);
            z-index: 2;
        }

        #ui-layer {
            position: absolute;
            bottom: 0; left: 0; right: 0;
            padding: 20px;
            z-index: 10;
            padding-bottom: calc(20px + env(safe-area-inset-bottom));
        }

        #dialog-box {
            background: rgba(26, 26, 46, 0.9);
            border: 1px solid rgba(129, 140, 248, 0.3);
            border-radius: 15px;
            padding: 20px;
            backdrop-filter: blur(10px);
            box-shadow: 0 -10px 30px rgba(0,0,0,0.5);
        }

        #speaker-name {
            color: #a5b4fc;
            font-weight: 700;
            font-size: 1.1rem;
            margin-bottom: 8px;
        }

        #text {
            font-size: 1rem;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .choice-btn {
            width: 100%;
            padding: 15px;
            margin-top: 10px;
            background: rgba(99, 102, 241, 0.2);
            border: 1px solid rgba(99, 102, 241, 0.5);
            border-radius: 10px;
            color: white;
            text-align: left;
            font-weight: 500;
            transition: all 0.3s;
        }

        .choice-btn:active {
            background: rgba(99, 102, 241, 0.5);
            transform: scale(0.98);
        }

        .title-screen {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: #1a1a2e;
            z-index: 100;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
            transition: opacity 1s;
        }

        .handwritten {
            font-family: 'Marck Script', cursive;
            font-size: 3.5rem;
            color: #f472b6;
            text-shadow: 0 0 20px rgba(244, 114, 182, 0.4);
            margin-bottom: 1rem;
        }

        .fade-out { opacity: 0; pointer-events: none; }
        .hidden { display: none !important; }
    </style>
</head>
<body>
    <div class="game-container">
        <!-- ТИТУЛЬНЫЙ ЭКРАН -->
        <div id="title-screen" class="title-screen">
            <h1 class="handwritten">Наша любовь</h1>
            <p class="text-indigo-300 tracking-[0.2em] text-sm mb-12 uppercase">История с 2004 года</p>
            <button onclick="startPlay()" class="bg-gradient-to-r from-rose-500 to-pink-600 px-10 py-4 rounded-full font-bold text-lg shadow-lg shadow-rose-500/30 active:scale-95 transition-transform">
                Начать историю 💕
            </button>
        </div>

        <div id="bg" class="scene-bg"></div>
        <div class="overlay"></div>

        <div id="ui-layer" class="hidden">
            <div id="dialog-box">
                <div id="speaker-name">Дмитрий</div>
                <div id="text">...</div>
                <div id="choices"></div>
            </div>
        </div>
    </div>

    <script>
        const scenes = [
            {
                bgClass: 'bg-2004-school',
                speaker: 'Дмитрий',
                text: '2004 год. Мне 10 лет. В классе появилась новая девочка. Она была просто шикарна! Мое сердце забилось чаще...',
                choices: [{ text: 'Она мне очень понравилась ❤️', next: 1 }]
            },
            {
                bgClass: 'bg-school-walk',
                speaker: 'Дмитрий',
                text: 'Мы начали общаться. Я провожал её до дома, носил портфель, помогал с уроками. Но тогда я был лишь верным другом...',
                choices: [{ text: 'Прошли школьные годы 😔', next: 2 }]
            },
            {
                bgClass: 'bg-separate-cities',
                speaker: 'Дмитрий',
                text: 'После школы жизнь развела нас. Разные города, новые знакомства. Связь оборвалась на долгих 12 лет...',
                choices: [{ text: 'Но судьба ждала своего часа...', next: 3 }]
            },
            {
                bgClass: 'bg-social-like',
                speaker: 'Дмитрий',
                text: '2016 год. Случайный лайк в соцсети перевернул всё. Мы начали переписываться ночами напролет, как тогда в школе.',
                choices: [{ text: 'Договориться о встрече в кафе ☕', next: 4 }]
            },
            {
                bgClass: 'bg-cafe-meet',
                speaker: 'Жена',
                text: 'Вечер в кафе. Мы смеялись, вспоминая детство. И вдруг я спросила: "А с*кс будет?". Ты ответил не раздумывая!',
                choices: [{ text: '"Да!" — и это было начало новой главы 😏', next: 5 }]
            },
            {
                bgClass: 'bg-dating',
                speaker: 'Дмитрий',
                text: 'Любовь вспыхнула ярче, чем когда-либо. Мы поняли, что 12 лет разлуки были лишь подготовкой к этому моменту.',
                choices: [{ text: 'Спустя год мы решили пожениться 💒', next: 6 }]
            },
            {
                bgClass: 'bg-wedding',
                speaker: 'Свадебный ведущий',
                text: 'Под звуки марша Мендельсона вы стали мужем и женой. Официально и навсегда.',
                choices: [{ text: 'Но впереди был самый важный шаг 💍', next: 7 }]
            },
            {
                bgClass: 'bg-wedding-ring',
                speaker: 'Финал',
                text: 'Венчание. Перед небом и землей вы закрепили свой союз. С 2004 года и на всю жизнь! Счастливого брака! ❤️',
                choices: [{ text: 'Прожить историю снова 🔄', next: 0 }]
            }
        ];

        let currentScene = 0;

        function startPlay() {
            document.getElementById('title-screen').classList.add('fade-out');
            setTimeout(() => {
                document.getElementById('title-screen').style.display = 'none';
                document.getElementById('ui-layer').classList.remove('hidden');
                updateScene();
            }, 1000);
        }

        function updateScene() {
            const scene = scenes[currentScene];
            const bg = document.getElementById('bg');
            const choicesContainer = document.getElementById('choices');
            
            // Плавная смена фона
            bg.style.opacity = 0;
            setTimeout(() => {
                bg.className = `scene-bg ${scene.bgClass}`;
                bg.style.opacity = 1;
            }, 300);
            
            document.getElementById('speaker-name').textContent = scene.speaker;
            document.getElementById('text').textContent = scene.text;
            
            choicesContainer.innerHTML = '';
            scene.choices.forEach(choice => {
                const btn = document.createElement('button');
                btn.className = 'choice-btn';
                btn.textContent = choice.text;
                btn.onclick = () => {
                    currentScene = choice.next;
                    updateScene();
                };
                choicesContainer.appendChild(btn);
            });
        }
    </script>
</body>
</html>
