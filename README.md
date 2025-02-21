<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>André ❤️ Sophie - Liebes-Countdown</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/particles.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@300;400;700&display=swap');

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(to right, #ff758c, #ff7eb3);
            overflow: hidden;
        }

        #particles-js {
            position: absolute;
            width: 100%;
            height: 100%;
        }

        .container {
            text-align: center;
            color: white;
            position: relative;
            z-index: 2;
        }

        h1 {
            font-size: 4em;
            font-family: 'Great Vibes', cursive;
            text-shadow: 2px 2px 10px rgba(0,0,0,0.3);
        }

        .countdown {
            font-size: 2.5em;
            font-weight: bold;
            margin-top: 20px;
            font-family: 'Poppins', sans-serif;
        }

        .heart {
            font-size: 5em;
            animation: heartbeat 1s infinite alternate;
        }

        @keyframes heartbeat {
            from { transform: scale(1); }
            to { transform: scale(1.2); }
        }
    </style>
</head>
<body>

    <div id="particles-js"></div>

    <div class="container">
        <h1>André ❤️ Sophie</h1>
        <div class="heart">💖</div>
        <div class="countdown" id="countdown">Lädt...</div>
        <audio autoplay loop>
            <source src="https://www.bensound.com/bensound-music/bensound-love.mp3" type="audio/mp3">
            Dein Browser unterstützt kein Audio.
        </audio>
    </div>

    <script>
        function updateCountdown() {
            const startDate = new Date("2022-01-27T00:00:00");
            const now = new Date();
            let diff = now - startDate;

            let seconds = Math.floor(diff / 1000) % 60;
            let minutes = Math.floor(diff / (1000 * 60)) % 60;
            let hours = Math.floor(diff / (1000 * 60 * 60)) % 24;
            let days = Math.floor(diff / (1000 * 60 * 60 * 24));

            document.getElementById("countdown").innerText = 
                `${days} Tage, ${hours} Stunden, ${minutes} Minuten, ${seconds} Sekunden`;

            gsap.to(".countdown", { scale: 1.1, duration: 0.3, yoyo: true, repeat: 1 });
        }

        setInterval(updateCountdown, 1000);
        updateCountdown();

        particlesJS("particles-js", {
            particles: {
                number: { value: 80, density: { enable: true, value_area: 800 } },
                color: { value: "#ffffff" },
                shape: { type: "circle" },
                opacity: { value: 0.7, random: true },
                size: { value: 3, random: true },
                move: { enable: true, speed: 2 }
            }
        });
    </script>
</body>
</html>
