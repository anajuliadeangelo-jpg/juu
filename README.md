<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora Moderna</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #0f172a;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .calculator {
            background-color: #1e293b;
            padding: 20px;
            border-radius: 16px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
            width: 320px;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        #display {
            width: 100%;
            height: 70px;
            background-color: #0f172a;
            color: #f8fafc;
            font-size: 2rem;
            text-align: right;
            padding: 0 16px;
            border: none;
            border-radius: 10px;
            margin-bottom: 20px;
            outline: none;
            box-sizing: border-box;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        button {
            background-color: #334155;
            color: #f8fafc;
            border: none;
            padding: 20px;
            font-size: 1.2rem;
            border-radius: 10px;
            cursor: pointer;
            transition: background-color 0.2s, transform 0.1s;
        }

        button:hover {
            background-color: #475569;
        }

        button:active {
            transform: scale(0.95);
        }

        .operator {
            background-color: #6366f1;
            color: #ffffff;
        }

        .operator:hover {
            background-color: #4f46e5;
        }

        .clear {
            background-color: #ef4444;
            color: #ffffff;
        }

        .clear:hover {
            background-color: #dc2626;
        }

        .equals {
            background-color: #10b981;
            color: #ffffff;
            grid-column: span 2;
        }

        .equals:hover {
            background-color: #059669;
        }
    </style>
</head>
<body>

    <div class="calculator">
        <input type="text" id="display" readonly value="0">
        
        <div class="buttons">
            <button class="clear" onclick="clearDisplay()">C</button>
            <button onclick="appendValue('/')" class="operator">÷</button>
            <button onclick="appendValue('*')" class="operator">×</button>
            <button onclick="backspace()" class="operator">⌫</button>

            <button onclick="appendValue('7')">7</button>
            <button onclick="appendValue('8')">8</button>
            <button onclick="appendValue('9')">9</button>
            <button onclick="appendValue('-')" class="operator">-</button>

            <button onclick="appendValue('4')">4</button>
            <button onclick="appendValue('5')">5</button>
            <button onclick="appendValue('6')">6</button>
            <button onclick="appendValue('+')" class="operator">+</button>

            <button onclick="appendValue('1')">1</button>
            <button onclick="appendValue('2')">2</button>
            <button onclick="appendValue('3')">3</button>
            <button onclick="calculate()" class="equals">=</button>

            <button onclick="appendValue('0')" style="grid-column: span 2;">0</button>
            <button onclick="appendValue('.')">.</button>
        </div>
    </div>

    <script>
        const display = document.getElementById('display');

        function appendValue(val) {
            if (display.value === '0' && val !== '.') {
                display.value = val;
            } else {
                display.value += val;
            }
        }

        function clearDisplay() {
            display.value = '0';
        }

        function backspace() {
            display.value = display.value.slice(0, -1);
            if (display.value === '') {
                display.value = '0';
            }
        }

        function calculate() {
            try {
                // Substitui os símbolos visuais pelos operadores matemáticos do JS
                let expression = display.value.replace(/×/g, '*').replace(/÷/g, '/');
                display.value = eval(expression);
            } catch (error) {
                display.value = 'Erro';
                setTimeout(clearDisplay, 1500);
            }
        }
    </script>

</body>
</html>
