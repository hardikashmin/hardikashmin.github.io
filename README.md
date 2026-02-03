# hardikashmin.github.io

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Forever Valentine ❤️</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <style>
        :root {
            --primary: #ff1a75;
            --secondary: #ff4d94;
            --bg: #fff0f5;
        }

        body {
            background: var(--bg);
            font-family: 'Georgia', serif;
            margin: 0;
            overflow-x: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        /* FLOATING HEARTS ANIMATION */
        .heart-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        /* THE PROPOSAL CARD */
        .card {
            background: rgba(255, 255, 255, 0.95);
            max-width: 550px;
            width: 90%;
            padding: 40px;
            border-radius: 40px;
            border: 8px solid #ffccd5;
            box-shadow: 0 20px 50px rgba(255, 26, 117, 0.3);
            text-align: center;
            animation: fadeIn 1.5s ease;
        }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }

        .couple-photo {
            width: 100%;
            height: 300px;
            object-fit: cover;
            border-radius: 25px;
            border: 4px solid var(--primary);
            margin-bottom: 25px;
        }

        h1 { color: var(--primary); font-size: 2.5rem; margin-bottom: 5px; text-shadow: 1px 1px 2px rgba(0,0,0,0.1); }
        h2 { color: var(--secondary); margin-top: 0; font-style: italic; }
        
        .story-text {
            color: #444;
            line-height: 1.8;
            font-size: 1.2rem;
            margin: 25px 0;
            padding: 0 10px;
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }

        button {
            padding: 18px 40px;
            font-size: 1.3rem;
            font-weight: bold;
            border: none;
            border-radius: 100px;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        #yesBtn {
            background: linear-gradient(45deg, #ff1a75, #ff80ab);
            color: white;
            box-shadow: 0 10px 20px rgba(255, 26, 117, 0.4);
        }

        #noBtn { background: #ffe5ec; color: #ff80ab; }

        button:hover { transform: scale(1.1); box-shadow: 0 15px 25px rgba(255, 26, 117, 0.5); }

        #success { display: none; }
        .heart-icon { color: var(--primary); font-size: 2rem; margin: 10px; }

    </style>
</head>
<body>

    <canvas class="heart-bg" id="heartCanvas"></canvas>

    <div class="card">
        <div id="proposal-ui">
            <img src="[url=https://postimg.cc/tZG4Q7Vz][img]https://i.postimg.cc/tZG4Q7Vz/Whats-App-Image-2026-02-03-at-11-06-45.jpg[/img][/url] https://postimg.cc/wyYj83sW https://i.postimg.cc/wyYj83sW/Whats-App-Image-2026-02-03-at-11-06-46.jpg https://postimg.cc/9RHQ5zq8][img]https://i.postimg.cc/9RHQ5zq8/Whats-App-Image-2026-02-03-at-11-06-46-(1).jpg" >


            
            <div class="heart-icon">❤️❤️❤️</div>
            <h1>To My Forever Valentine,</h1>
            <h2>You are my world...</h2>

            <div class="Our Story:
            Baby before i met you i never knew what the true meaning of love was, i never knew that one girl would change my life so much until i met you.
            since the day we started talking all i have been filled with is joy, you bring out the best out of me and a part that i never knew was inside me,
            you truely are a blessing from god baby, the way you make me laugh, smile, happy, (freaky), and just feel like the strongest man on earth. i dont know how to thank you enough for what you have done              my baby, you have healed me in a way i never thought was possible i love you so much my baby.">
                Every second with you is a gift. I promise to love you, cherish you, and make you laugh every single day for the rest of our lives.
            </div>

            <div class="buttons">
                <button id="yesBtn" onclick="celebrate()">YES! 💍</button>
                <button id="noBtn" onmouseover="dodge()">No</button>
            </div>
        </div>

        <div id="success">
            <h1 style="font-size: 3.5rem;">YES! 🎉</h1>
            <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExNHJpbmZ1YXJ5Z3Z0ZWF4bmZxeW56ZzR5eHh4eHh4eHh4eHh4eHh4JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1n/KztT2c4u8mYYUiCiNR/giphy.gif" style="width:100%; border-radius: 20px;">
            <p style="font-size: 1.5rem; color: #ff1a75; font-weight: bold;">I love you more than words can say!</p>
            <div class="heart-icon">💖💖💖</div>
        </div>
    </div>

    <script>
        // 1. Floating Hearts Animation
        const canvas = document.getElementById('heartCanvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const hearts = [];
        function createHeart() {
            return {
                x: Math.random() * canvas.width,
                y: canvas.height + 20,
                size: Math.random() * 20 + 10,
                speed: Math.random() * 2 + 1,
                opacity: Math.random() * 0.5 + 0.2
            };
        }

        function drawHearts() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            hearts.forEach((h, i) => {
                h.y -= h.speed;
                ctx.fillStyle = `rgba(255, 26, 117, ${h.opacity})`;
                ctx.font = `${h.size}px serif`;
                ctx.fillText('❤️', h.x, h.y);
                if (h.y < -20) hearts[i] = createHeart();
            });
            requestAnimationFrame(drawHearts);
        }
        for(let i=0; i<30; i++) hearts.push(createHeart());
        drawHearts();

        // 2. Button Dodge logic
        function dodge() {
            const btn = document.getElementById('noBtn');
            const x = Math.random() * (window.innerWidth - 150);
            const y = Math.random() * (window.innerHeight - 100);
            btn.style.position = 'fixed';
            btn.style.left = x + 'px';
            btn.style.top = y + 'px';
        }

        // 3. Success Logic
        function celebrate() {
            document.getElementById('proposal-ui').style.display = 'none';
            document.getElementById('success').style.display = 'block';
            
            // Trigger Confetti
            var duration = 15 * 1000;
            var animationEnd = Date.now() + duration;
            var defaults = { startVelocity: 30, spread: 360, ticks: 60, zIndex: 0 };

            function randomInRange(min, max) { return Math.random() * (max - min) + min; }

            var interval = setInterval(function() {
                var timeLeft = animationEnd - Date.now();
                if (timeLeft <= 0) return clearInterval(interval);
                var particleCount = 50 * (timeLeft / duration);
                confetti(Object.assign({}, defaults, { particleCount, origin: { x: randomInRange(0.1, 0.3), y: Math.random() - 0.2 } }));
                confetti(Object.assign({}, defaults, { particleCount, origin: { x: randomInRange(0.7, 0.9), y: Math.random() - 0.2 } }));
            }, 250);
        }
    </script>
</body>
</html>
