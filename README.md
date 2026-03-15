<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CR7 Live Counter | Al-Nassr & Portugal</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@700&family=Poppins:wght@300;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --nassr-yellow: #f6ca15;
            --nassr-blue: #0054a6;
            --portugal-red: #da291c;
            --portugal-green: #00662d;
            --dark-bg: #050505;
        }

        body {
            background-color: var(--dark-bg);
            color: white;
            font-family: 'Poppins', sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            margin: 0;
            /* Efeito de brilho de fundo com as cores de Portugal */
            background: radial-gradient(circle at top left, rgba(0, 102, 45, 0.15), transparent),
                        radial-gradient(circle at bottom right, rgba(218, 41, 28, 0.15), transparent);
        }

        header h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.8rem;
            text-align: center;
            margin-bottom: 20px;
            text-transform: uppercase;
        }

        .yellow { color: var(--nassr-yellow); }
        .blue { color: var(--nassr-blue); }

        .main-container {
            background: rgba(255, 255, 255, 0.03);
            padding: 50px 80px;
            border-radius: 20px;
            border-top: 5px solid var(--nassr-yellow);
            border-bottom: 5px solid var(--portugal-red);
            text-align: center;
            box-shadow: 0 15px 40px rgba(0,0,0,0.5);
            backdrop-filter: blur(10px);
        }

        #goal-label {
            font-size: 0.9rem;
            color: #aaa;
            letter-spacing: 4px;
            font-weight: 600;
        }

        #total-goals {
            font-family: 'Orbitron', sans-serif;
            font-size: 130px;
            color: white;
            margin: 10px 0;
            text-shadow: 0 0 30px rgba(246, 202, 21, 0.3);
        }

        .btn-group {
            display: flex;
            gap: 15px;
            margin-top: 30px;
        }

        .btn {
            border: none;
            padding: 12px 25px;
            font-family: 'Poppins', sans-serif;
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            transition: 0.3s;
        }

        .btn-nassr { background: var(--nassr-yellow); color: var(--nassr-blue); }
        .btn-portugal { background: var(--portugal-red); color: white; }

        .btn:hover { transform: translateY(-5px); opacity: 0.9; }

        footer {
            margin-top: 40px;
            font-size: 0.8rem;
            color: #555;
        }
    </style>
</head>
<body>

    <header>
        <h1>CRISTIANO <span class="yellow">RONALDO</span></h1>
    </header>

    <main class="main-container">
        <div id="goal-label">TOTAL DE GOLS NA CARREIRA</div>
        <div id="total-goals" data-target="915">0</div>
        
        <div class="btn-group">
            <button class="btn btn-nassr" onclick="siuu('nassr')">SIUUU AL-NASSR!</button>
            <button class="btn btn-portugal" onclick="siuu('portugal')">SIUUU PORTUGAL!</button>
        </div>
    </main>

    <footer>
        <p>Desenvolvido para acompanhar o maior de todos os tempos.</p>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.5.1/dist/confetti.browser.min.js"></script>
    <script>
        const counter = document.getElementById('total-goals');

        function animate() {
            const target = +counter.getAttribute('data-target');
            const current = +counter.innerText;
            if (current < target) {
                counter.innerText = Math.ceil(current + (target / 100));
                setTimeout(animate, 25);
            } else {
                counter.innerText = target;
            }
        }

        function siuu(tipo) {
            let cores = tipo === 'nassr' ? ['#f6ca15', '#0054a6'] : ['#da291c', '#00662d'];
            confetti({
                particleCount: 100,
                spread: 70,
                colors: cores
            });
            
            // Simula aumento de gol para teste visual
            let val = parseInt(counter.getAttribute('data-target'));
            counter.setAttribute('data-target', val + 1);
            animate();
        }

        window.onload = animate;
    </script>
</body>
</html>
