<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f3f4f6;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .calculator {
      background: #ffffff;
      border-radius: 20px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
      padding: 20px;
      width: 320px;
    }

    .display {
      background: #f9f9f9;
      border-radius: 10px;
      padding: 15px;
      text-align: right;
      font-size: 24px;
      margin-bottom: 20px;
      box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.1);
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    .button {
      background: #4caf50;
      color: #ffffff;
      border: none;
      border-radius: 10px;
      padding: 15px;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.3s;
    }

    .button:hover {
      background: #45a049;
    }

    .button.operator {
      background: #ff9800;
    }

    .button.operator:hover {
      background: #fb8c00;
    }

    .button.clear {
      background: #f44336;
    }

    .button.clear:hover {
      background: #e53935;
    }

    .button.vivek {
      background: #2196f3;
    }

    .button.vivek:hover {
      background: #1e88e5;
    }

    .message {
      text-align: center;
      font-size: 14px;
      color: #555;
      margin-top: 10px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div id="display" class="display">0</div>
    <div class="buttons">
      <button class="button clear" onclick="clearDisplay()">C</button>
      <button class="button" onclick="backspace()">←</button>
      <button class="button vivek" onclick="showVivek()">V</button>
      <button class="button operator" onclick="appendValue('/')">÷</button>

      <button class="button" onclick="appendValue('7')">7</button>
      <button class="button" onclick="appendValue('8')">8</button>
      <button class="button" onclick="appendValue('9')">9</button>
      <button class="button operator" onclick="appendValue('*')">×</button>

      <button class="button" onclick="appendValue('4')">4</button>
      <button class="button" onclick="appendValue('5')">5</button>
      <button class="button" onclick="appendValue('6')">6</button>
      <button class="button operator" onclick="appendValue('-')">−</button>

      <button class="button" onclick="appendValue('1')">1</button>
      <button class="button" onclick="appendValue('2')">2</button>
      <button class="button" onclick="appendValue('3')">3</button>
      <button class="button operator" onclick="appendValue('+')">+</button>

      <button class="button" onclick="appendValue('0')">0</button>
      <button class="button" onclick="appendValue('.')">.</button>
      <button class="button operator" onclick="calculateResult()">=</button>
    </div>
    <div id="vivek-message" class="message"></div>
  </div>

  <script>
    const display = document.getElementById('display');
    const vivekMessage = document.getElementById('vivek-message');

    function appendValue(value) {
      if (display.innerText === '0') {
        display.innerText = value;
      } else {
        display.innerText += value;
      }
    }

    function clearDisplay() {
      display.innerText = '0';
      vivekMessage.innerText = ""; // Clear Vivek's message
    }

    function backspace() {
      if (display.innerText.length === 1 || display.innerText === '0') {
        display.innerText = '0';
      } else {
        display.innerText = display.innerText.slice(0, -1);
      }
    }

    function calculateResult() {
      try {
        display.innerText = eval(display.innerText);
      } catch (error) {
        display.innerText = 'Error';
      }
    }

    function showVivek() {
      // When the V button is pressed, display "Created by Vivek Maurya" in the display
      display.innerText = "Created by Vivek Maurya";
    }
  </script>
</body>
</html>
