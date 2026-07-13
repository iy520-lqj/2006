<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>❤️ 致亲爱的你 ❤️</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            width: 100vw;
            height: 100vh;
            overflow: hidden;
            background: linear-gradient(135deg, #fce4ec, #f8bbd0, #f48fb1);
            font-family: 'Segoe UI', 'PingFang SC', 'Microsoft YaHei', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
            position: relative;
        }

        canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .container {
            position: relative;
            z-index: 10;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
        }

        .heart {
            position: relative;
            width: 180px;
            height: 180px;
            margin-bottom: 30px;
            animation: heartbeat 1.2s ease-in-out infinite;
            filter: drop-shadow(0 10px 25px rgba(244, 67, 54, 0.5));
            transition: transform 0.6s cubic-bezier(0.68, -0.55, 0.27, 1.55), opacity 0.4s;
        }

        .heart.hide {
            transform: scale(0) rotate(45deg);
            opacity: 0;
        }

        .heart::before,
        .heart::after {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            background: #e91e63;
            border-radius: 50%;
        }

        .heart::before {
            top: 0;
            left: -50%;
        }

        .heart::after {
            top: -50%;
            left: 0;
        }

        .heart-body {
            position: absolute;
            width: 100%;
            height: 100%;
            background: #e91e63;
            transform: rotate(45deg);
            top: 0;
            left: 0;
        }

        @keyframes heartbeat {
            0%   { transform: scale(1); }
            14%  { transform: scale(1.1); }
            28%  { transform: scale(1); }
            42%  { transform: scale(1.1); }
            70%  { transform: scale(1); }
            100% { transform: scale(1); }
        }

        .hint {
            font-size: 1.6rem;
            color: #fff;
            text-shadow: 0 2px 10px rgba(233, 30, 99, 0.5);
            margin-bottom: 25px;
            letter-spacing: 2px;
            animation: fadeInUp 1.2s ease;
        }

        .reveal-btn {
            background: #fff;
            color: #e91e63;
            border: none;
            padding: 15px 45px;
            font-size: 1.3rem;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            letter-spacing: 2px;
            box-shadow: 0 8px 25px rgba(233, 30, 99, 0.4);
            transition: all 0.3s ease;
            animation: fadeInUp 1.2s ease 0.2s both;
            outline: none;
        }

        .reveal-btn:hover {
            background: #e91e63;
            color: #fff;
            transform: translateY(-3px);
            box-shadow: 0 15px 30px rgba(233, 30, 99, 0.6);
        }

        .reveal-btn:active {
            transform: scale(0.95);
        }

        .card {
            display: none;
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(15px);
            border-radius: 30px;
            padding: 40px 30px;
            width: 90%;
            max-width: 400px;
            box-shadow: 0 30px 50px rgba(233, 30, 99, 0.3);
            flex-direction: column;
            align-items: center;
            animation: cardPop 0.6s cubic-bezier(0.68, -0.55, 0.27, 1.55);
            margin-top: 20px;
        }

        .card.show {
            display: flex;
        }

        .card .message {
            font-size: 1.8rem;
            color: #d81b60;
            font-weight: bold;
            margin-bottom: 30px;
            text-shadow: 0 2px 10px rgba(233, 30, 99, 0.2);
            line-height: 1.4;
        }

        .card .buttons {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .yes-btn, .no-btn {
            border: none;
            padding: 14px 35px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            letter-spacing: 1px;
            transition: all 0.3s ease;
            outline: none;
            min-width: 120px;
        }

        .yes-btn {
            background: #e91e63;
            color: #fff;
            box-shadow: 0 8px 20px rgba(233, 30, 99, 0.5);
        }

        .yes-btn:hover {
            background: #c2185b;
            transform: scale(1.05);
            box-shadow: 0 12px 25px rgba(233, 30, 99, 0.7);
        }

        .no-btn {
            background: #eee;
            color: #777;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            position: relative;
            transition: left 0.2s ease, top 0.2s ease, background 0.3s;
        }

        .no-btn:hover {
            background: #ddd;
        }

        .card .success-message {
            display: none;
            font-size: 2rem;
            color: #e91e63;
            font-weight: bold;
            animation: heartBeat 0.8s ease infinite;
        }

        @keyframes cardPop {
            0% { transform: scale(0) rotate(-10deg); opacity: 0; }
            80% { transform: scale(1.05) rotate(2deg); opacity: 1; }
            100% { transform: scale(1) rotate(0deg); opacity: 1; }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes heartBeat {
            0% { transform: scale(1); }
            25% { transform: scale(1.1); }
            50% { transform: scale(1); }
            75% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        .hidden {
            display: none !important;
        }
    </style>
</head>
<body>
    <canvas id="canvas"></canvas>

    <div class="container" id="container">
        <div class="heart" id="heart">
            <div class="heart-body"></div>
        </div>

        <p class="hint" id="hintText">我有一句悄悄话想对你说...</p>
        
        <button class="reveal-btn" id="revealBtn">💌 点我</button>

        <div class="card" id="card">
            <p class="message" id="cardMessage">我喜欢你<br>可以做我女朋友吗？</p>
            <div class="buttons" id="btnGroup">
                <button class="yes-btn" id="yesBtn">好呀 ❤️</button>
                <button class="no-btn" id="noBtn">考虑一下...</button>
            </div>
            <p class="success-message" id="successMsg">耶！我也喜欢你！💖</p>
        </div>
    </div>

    <script>
        (function() {
            const canvas = document.getElementById('canvas');
            const ctx = canvas.getContext('2d');
            let width, height;
            let particles = [];
            const maxParticles = 120;
            let animationId;
            let particleActive = false;

            function resizeCanvas() {
                width = window.innerWidth;
                height = window.innerHeight;
                canvas.width = width;
                canvas.height = height;
            }
            window.addEventListener('resize', resizeCanvas);
            resizeCanvas();

            function drawHeartShape(ctx, x, y, size, alpha) {
                ctx.save();
                ctx.globalAlpha = alpha;
                ctx.fillStyle = '#e91e63';
                ctx.beginPath();
                const topCurveHeight = size * 0.3;
                ctx.moveTo(x, y + topCurveHeight);
                ctx.bezierCurveTo(x, y, x - size / 2, y, x - size / 2, y + topCurveHeight);
                ctx.bezierCurveTo(x - size / 2, y + (size + topCurveHeight) / 1.8, x, y + (size + topCurveHeight) / 1.6, x, y + size);
                ctx.bezierCurveTo(x, y + (size + topCurveHeight) / 1.6, x + size / 2, y + (size + topCurveHeight) / 1.8, x + size / 2, y + topCurveHeight);
                ctx.bezierCurveTo(x + size / 2, y, x, y, x, y + topCurveHeight);
                ctx.closePath();
                ctx.fill();
                ctx.restore();
            }

            class Particle {
                constructor(x, y, vx, vy, size, life) {
                    this.x = x;
                    this.y = y;
                    this.vx = vx;
                    this.vy = vy;
                    this.size = size;
                    this.life = life;
                    this.maxLife = life;
                    this.alpha = 1;
                }

                update() {
                    this.x += this.vx;
                    this.y += this.vy;
                    this.vy += 0.15;
                    this.life--;
                    this.alpha = Math.max(0, this.life / this.maxLife);
                }

                draw(ctx) {
                    drawHeartShape(ctx, this.x, this.y, this.size, this.alpha);
                }

                isDead() {
                    return this.life <= 0 || this.y > height + 50 || this.x < -50 || this.x > width + 50;
                }
            }

            function burstParticles(x, y, count = 40) {
                for (let i = 0; i < count; i++) {
                    const angle = Math.random() * Math.PI * 2;
                    const speed = 2 + Math.random() * 6;
                    const vx = Math.cos(angle) * speed;
                    const vy = Math.sin(angle) * speed - 2;
                    const size = 8 + Math.random() * 18;
                    const life = 50 + Math.floor(Math.random() * 60);
                    particles.push(new Particle(x, y, vx, vy, size, life));
                }
            }

            function spawnFloatingHeart() {
                const x = Math.random() * width;
                const y = -30;
                const vx = (Math.random() - 0.5) * 1.2;
                const vy = 0.8 + Math.random() * 2.5;
                const size = 10 + Math.random() * 25;
                const life = 120 + Math.floor(Math.random() * 100);
                particles.push(new Particle(x, y, vx, vy, size, life));
            }

            function animate() {
                ctx.clearRect(0, 0, width, height);
                if (particleActive) {
                    if (Math.random() < 0.25 && particles.length < maxParticles) {
                        spawnFloatingHeart();
                    }
                } else if (Math.random() < 0.03 && particles.length < 30) {
                    spawnFloatingHeart();
                }

                for (let i = particles.length - 1; i >= 0; i--) {
                    const p = particles[i];
                    p.update();
                    p.draw(ctx);
                    if (p.isDead()) {
                        particles.splice(i, 1);
                    }
                }

                animationId = requestAnimationFrame(animate);
            }

            animate();

            const heartEl = document.getElementById('heart');
            const hintEl = document.getElementById('hintText');
            const revealBtn = document.getElementById('revealBtn');
            const card = document.getElementById('card');
            const cardMessage = document.getElementById('cardMessage');
            const btnGroup = document.getElementById('btnGroup');
            const yesBtn = document.getElementById('yesBtn');
            const noBtn = document.getElementById('noBtn');
            const successMsg = document.getElementById('successMsg');

            function getHeartCenter() {
                const rect = heartEl.getBoundingClientRect();
                return {
                    x: rect.left + rect.width / 2,x：rect.left + rect.width / 2,
                    y: rect.top + rect.height / 2
                };
            }

            revealBtn.addEventListener('click', () => {
                heartEl.classList.add('hide');
                hintEl.classList.add('hidden');
                revealBtn.classList.add('hidden');
                const center = getHeartCenter();
                burstParticles(center.x, center.y, 50);
                particleActive = true;
                setTimeout(() => {
                    card.classList.add('show');
                }, 400);
            });

            yesBtn.addEventListener('click', () => {
                cardMessage.classList.add('hidden');
                btnGroup.classList.add('hidden');
                successMsg.style.display = 'block';
                const center = getHeartCenter();
                burstParticles(center.x, center.y, 80);
                particleActive = true;
                setTimeout(() => {
                    successMsg.textContent = '我们在一起吧！😘';
                }, 1500);
            });

            function moveNoButton() {
                const btn = noBtn;
                const btnWidth = btn.offsetWidth;
                const btnHeight = btn.offsetHeight;
                const maxX = window.innerWidth - btnWidth - 20;
                const maxY = window.innerHeight - btnHeight - 20;
                const randomX = Math.max(10, Math.random() * maxX);
                const randomY = Math.max(10, Math.random() * maxY);
                btn.style.position = 'fixed';
                btn.style.left = randomX + 'px';
                btn.style.top = randomY + 'px';
                btn.style.zIndex = '999';
            }

            noBtn.addEventListener('mouseenter', moveNoButton);
            noBtn.addEventListener('touchstart', (e) => {
                e.preventDefault();
                moveNoButton();
                noBtn.style.transform = 'scale(0.9)';
                setTimeout(() => { noBtn.style.transform = ''; }, 150);
            });

            noBtn.addEventListener('click', (e) => {
                e.stopPropagation();
                moveNoButton();
                const originalText = noBtn.textContent;
                noBtn.textContent = '再想想嘛~';
                noBtn.style.background = '#fce4ec';
                setTimeout(() => {
                    noBtn.textContent = originalText;
                    noBtn.style.background = '#eee';
                }, 800);
            });

            card.addEventListener('click', (e) => {
                e.stopPropagation();
            });

            window.addEventListener('resize', () => {
                if (noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.pos如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {如果（noBtn.style.position === 'fixed') {
                    const btnRect = noBtn.getBoundingClientRect();
                    if (btnRect.right > window.innerWidth || btnRect.bottom > window.innerHeight || btnRect.left < 0 || btnRect.top < 0) {
                        moveNoButton();
                    }
                }
            });
        })();
    </script>
</body>
</html>
