# webgame.github.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hamster Kombat</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }
        #game {
            text-align: center;
        }
        #player, #enemy {
            display: inline-block;
            margin: 20px;
        }
        .health-bar {
            width: 200px;
            height: 20px;
            background-color: red;
            margin: 10px 0;
        }
        .health {
            height: 100%;
            background-color: blue;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div id="game">
        <h1>Hamster Kombat</h1>
        <div id="player">
            <h2>Player</h2>
            <div class="health-bar">
                <div id="player-health" class="health"></div>
            </div>
        </div>
        <div id="enemy">
            <h2>Enemy</h2>
            <div class="health-bar">
                <div id="enemy-health" class="health"></div>
            </div>
        </div>
        <button onclick="fight()">Fight</button>
        <p id="result"></p>
    </div>

    <script>
        let playerHealth = 100;
        let enemyHealth = 100;

        function updateHealthBars() {
            document.getElementById('player-health').style.width = playerHealth + '%';
            document.getElementById('enemy-health').style.width = enemyHealth + '%';
        }

        function fight() {
            const playerDamage = Math.floor(Math.random() * 20) + 1;
            const enemyDamage = Math.floor(Math.random() * 20) + 1;

            enemyHealth -= playerDamage;
            playerHealth -= enemyDamage;

            updateHealthBars();

            let resultText = `You dealt ${playerDamage} damage. The enemy dealt ${enemyDamage} damage.`;
            
            if (playerHealth <= 0 && enemyHealth <= 0) {
                resultText += " It's a draw!";
            } else if (playerHealth <= 0) {
                resultText += " You lose!";
            } else if (enemyHealth <= 0) {
                resultText += " You win!";
            }

            document.getElementById('result').innerText = resultText;

            if (playerHealth <= 0 || enemyHealth <= 0) {
                document.querySelector('button').disabled = true;
            }
        }

        updateHealthBars();
    </script>
</body>
</html>
