<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rock Paper Scissors</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #f0f0f0;
        }
        h1 {
            color: #333;
        }
        .options {
            display: flex;
            gap: 10px;
        }
        .option {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border: 2px solid #333;
            border-radius: 5px;
            background-color: #fff;
            transition: background-color 0.3s;
        }
        .option:hover {
            background-color: #ddd;
        }
        #result {
            margin-top: 20px;
            font-size: 18px;
            color: #333;
        }
    </style>
</head>
<body>
    <h1>Rock Paper Scissors</h1>
    <div class="options">
        <button class="option">Rock</button>
        <button class="option">Paper</button>
        <button class="option">Scissors</button>
    </div>
    <p id="result"></p>

    <script>
        const options = document.querySelectorAll('.option');
        const result = document.getElementById('result');
        const choices = ['Rock', 'Paper', 'Scissors'];

        options.forEach(option => {
            option.addEventListener('click', function() {
                const playerChoice = this.textContent;
                const computerChoice = choices[Math.floor(Math.random() * 3)];
                result.textContent = `Player: ${playerChoice} - Computer: ${computerChoice}`;
                determineWinner(playerChoice, computerChoice);
            });
        });

        function determineWinner(player, computer) {
            if (player === computer) {
                result.textContent += ' - It\'s a draw!';
            } else if (
                (player === 'Rock' && computer === 'Scissors') ||
                (player === 'Paper' && computer === 'Rock') ||
                (player === 'Scissors' && computer === 'Paper')
            ) {
                result.textContent += ' - You win!';
            } else {
                result.textContent += ' - You lose!';
            }
        }
    </script>
</body>
</html>
