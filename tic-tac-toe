<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tic Tac Toe</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .board {
            display: grid;
            grid-template-columns: repeat(3, 100px);
            grid-template-rows: repeat(3, 100px);
            gap: 5px;
            justify-content: center;
            margin-top: 20px;
        }
        .cell {
            width: 100px;
            height: 100px;
            background-color: #f0f0f0;
            font-size: 36px;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            border: 2px solid #ccc;
        }
        .cell:hover {
            background-color: #e0e0e0;
        }
        .cell.disabled {
            pointer-events: none;
            background-color: #d0d0d0;
        }
        .message {
            margin-top: 20px;
            font-size: 24px;
        }
    </style>
</head>
<body>
    <h1>Tic Tac Toe</h1>
    <div class="board" id="board"></div>
    <div class="message" id="message"></div>

    <script>
        const boardElement = document.getElementById('board');
        const messageElement = document.getElementById('message');
        let board = Array(3).fill().map(() => Array(3).fill(null));
        let currentPlayer = 'X';

        function createBoard() {
            boardElement.innerHTML = '';
            for (let row = 0; row < 3; row++) {
                for (let col = 0; col < 3; col++) {
                    const cell = document.createElement('div');
                    cell.classList.add('cell');
                    cell.dataset.row = row;
                    cell.dataset.col = col;
                    cell.addEventListener('click', onCellClick);
                    boardElement.appendChild(cell);
                }
            }
        }

        function onCellClick(event) {
            const row = event.target.dataset.row;
            const col = event.target.dataset.col;

            if (!board[row][col]) {
                board[row][col] = currentPlayer;
                event.target.textContent = currentPlayer;
                event.target.classList.add('disabled');

                if (checkWinner()) {
                    messageElement.textContent = `${currentPlayer} wins!`;
                    disableBoard();
                } else if (checkDraw()) {
                    messageElement.textContent = 'It\'s a draw!';
                } else {
                    currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
                }
            }
        }

        function checkWinner() {
            // Row and column checks
            for (let i = 0; i < 3; i++) {
                if (board[i][0] && board[i][0] === board[i][1] && board[i][1] === board[i][2]) return true;
                if (board[0][i] && board[0][i] === board[1][i] && board[1][i] === board[2][i]) return true;
            }
            // Diagonal checks
            if (board[0][0] && board[0][0] === board[1][1] && board[1][1] === board[2][2]) return true;
            if (board[0][2] && board[0][2] === board[1][1] && board[1][1] === board[2][0]) return true;

            return false;
        }

        function checkDraw() {
            return board.flat().every(cell => cell !== null);
        }

        function disableBoard() {
            document.querySelectorAll('.cell').forEach(cell => {
                cell.classList.add('disabled');
            });
        }

        createBoard();
    </script>
</body>
</html>
