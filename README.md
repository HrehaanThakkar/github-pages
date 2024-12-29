//simple calculator
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
        }
        .calculator {
            border: 1px solid #ccc;
            padding: 20px;
            border-radius: 10px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .display {
            width: 100%;
            height: 50px;
            background-color: #222;
            color: #fff;
            text-align: right;
            padding: 10px;
            font-size: 24px;
            border-radius: 5px;
            margin-bottom: 10px;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        .button {
            padding: 20px;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            background-color: #f0f0f0;
            transition: background-color 0.3s;
        }
        .button:hover {
            background-color: #ddd;
        }
        .button.operator {
            background-color: #ff9500;
            color: #fff;
        }
        .button.operator:hover {
            background-color: #e08900;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button class="button" onclick="clearDisplay()">C</button>
            <button class="button" onclick="deleteLast()">DEL</button>
            <button class="button operator" onclick="appendOperator('/')">/</button>
            <button class="button operator" onclick="appendOperator('*')">*</button>
            <button class="button" onclick="appendNumber('7')">7</button>
            <button class="button" onclick="appendNumber('8')">8</button>
            <button class="button" onclick="appendNumber('9')">9</button>
            <button class="button operator" onclick="appendOperator('-')">-</button>
            <button class="button" onclick="appendNumber('4')">4</button>
            <button class="button" onclick="appendNumber('5')">5</button>
            <button class="button" onclick="appendNumber('6')">6</button>
            <button class="button operator" onclick="appendOperator('+')">+</button>
            <button class="button" onclick="appendNumber('1')">1</button>
            <button class="button" onclick="appendNumber('2')">2</button>
            <button class="button" onclick="appendNumber('3')">3</button>
            <button class="button" onclick="appendNumber('0')">0</button>
            <button class="button" onclick="appendNumber('.')">.</button>
            <button class="button operator" onclick="calculateResult()">=</button>
        </div>
    </div>

    <script>
        const display = document.getElementById('display');

        function clearDisplay() {
            display.innerText = '0';
        }

        function deleteLast() {
            if (display.innerText.length > 1) {
                display.innerText = display.innerText.slice(0, -1);
            } else {
                display.innerText = '0';
            }
        }

        function appendNumber(number) {
            if (display.innerText === '0') {
                display.innerText = number;
            } else {
                display.innerText += number;
            }
        }

        function appendOperator(operator) {
            display.innerText += operator;
        }

        function calculateResult() {
            try {
                display.innerText = eval(display.innerText);
            } catch {
                display.innerText = 'Error';
            }
        }
    </script>
</body>
</html>
