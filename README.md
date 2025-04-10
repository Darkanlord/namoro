<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tempo de Namoro</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;500&family=Pacifico&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background: linear-gradient(135deg, #d4c7c7, #fad0c4);
            color: #333;
            text-align: center;
            padding: 50px;
            margin: 0;
        }
        h1 {
            font-family: 'Pacifico', cursive;
            color: #ff69b4;
            font-size: 48px;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
        }
        .container {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2);
            padding: 40px;
            max-width: 600px;
            margin: auto;
            animation: fadeIn 1.5s ease-in-out;
        }
        .time {
            font-size: 32px;
            color: #4a90e2;
            margin-top: 20px;
            font-weight: 500;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.1);
        }
        footer {
            margin-top: 30px;
            font-size: 14px;
            color: #555;
        }
        footer p {
            font-style: italic;
        }
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        .heart {
            color: #ff69b4;
            font-size: 24px;
            margin: 10px 0;
            animation: pulse 1.5s infinite;
        }
        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.2);
            }
        }
        .dark-theme {
            background: linear-gradient(135deg, #2c3e50, #4ca1af);
            color: #fff;
        }
        .dark-theme .container {
            background: rgba(0, 0, 0, 0.8);
            color: #fff;
        }
        @media (max-width: 600px) {
            h1 {
                font-size: 32px;
            }
            .container {
                padding: 20px;
            }
            .time {
                font-size: 24px;
            }
        }
    </style>
</head>
<body>
    <button id="toggle-theme">Alternar Tema</button>
    <div class="container">
        <h1>Tempo de Namoro de Samuel e Andrya</h1>
        <div class="heart">❤️</div>
        <div class="time" id="tempo"></div>
        <div id="aniversario" class="time"></div>
    </div>
    <footer>
        <p>Desde 29 de Outubro de 2016</p>
    </footer>

    <script>
        // Data de início do namoro
        const dataInicio = new Date('2016-10-29T00:00:00');

        // Alternar tema claro/escuro
        const body = document.body;
        const button = document.getElementById('toggle-theme');
        button.addEventListener('click', () => {
            body.classList.toggle('dark-theme');
        });

        // Função para calcular o tempo de namoro
        function calcularTempo() {
            const agora = new Date();
            const tempo = agora - dataInicio; // diferença em milissegundos

            const anos = agora.getFullYear() - dataInicio.getFullYear();
            const meses = agora.getMonth() - dataInicio.getMonth() + (anos * 12);
            const dias = Math.floor(tempo / (1000 * 60 * 60 * 24));
            const horas = Math.floor((tempo % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutos = Math.floor((tempo % (1000 * 60 * 60)) / (1000 * 60));
            const segundos = Math.floor((tempo % (1000 * 60)) / 1000);

            document.getElementById('tempo').innerHTML = 
                `${anos} anos, ${meses % 12} meses, ${dias} dias, ${horas} horas, ${minutos} minutos e ${segundos} segundos`;
        }

        // Função para calcular o próximo aniversário
        function calcularProximoAniversario() {
            const agora = new Date();
            const proximoAniversario = new Date(agora.getFullYear(), 9, 29); // 29 de Outubro
            if (agora > proximoAniversario) {
                proximoAniversario.setFullYear(agora.getFullYear() + 1);
            }

            const tempoRestante = proximoAniversario - agora;
            const dias = Math.floor(tempoRestante / (1000 * 60 * 60 * 24));
            const horas = Math.floor((tempoRestante % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutos = Math.floor((tempoRestante % (1000 * 60 * 60)) / (1000 * 60));
            const segundos = Math.floor((tempoRestante % (1000 * 60)) / 1000);

            document.getElementById('aniversario').innerHTML = 
                `Faltam ${dias} dias, ${horas} horas, ${minutos} minutos e ${segundos} segundos para o próximo aniversário!`;
        }

        // Atualiza o tempo a cada segundo
        setInterval(calcularTempo, 1000);
        setInterval(calcularProximoAniversario, 1000);
        calcularTempo(); // Chama a função uma vez para inicializar
        calcularProximoAniversario(); // Inicializa o cálculo do próximo aniversário
    </script>
</body>
</html>
