# ai
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>碳稅計算</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }

        input, select, button {
            font-size: 16px;
            margin: 5px;
            padding: 5px;
        }

        #history {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h2>Multiplication Calculator</h2>
    <select id="multiplicand">
        <option value="6.4">臺灣/6.4</option>
        <option value="2.17">日本/2.17</option>
        <option value="10.28">中國/10.28</option>
        <option value="3.77">新加坡/3.77</option>
        <option value="98.1">馬來西亞/98.1</option>
        <option value="8.93">南非/8.93</option>
        <option value="5.06">哥倫比亞/5.06</option>
        <option value="5">智利/5</option>
        <option value="0.08">波蘭/0.08</option>
        <option value="0.82">烏克蘭/0.82</option>
        <option value="3.34">阿根廷/3.34</option>
        <option value="4.07">墨西哥/4.07</option>
        <option value="16.31">西班牙/16.31</option>
        <option value="16.31">拉脫維亞/16.31</option>
        <option value="22.28">英國/22.28</option>
        <option value="26.01">葡萄牙/26.01</option>
        <option value="26.53">丹麥/26.53</option>
        <option value="38.53">冰島/38.53</option>
        <option value="44.59">愛爾蘭/44.59</option>
        <option value="48.03">加拿大/48.03</option>
        <option value="48.11">盧森堡/48.11</option>
        <option value="48.5">法國/48.5</option>
        <option value="55.59">荷蘭/55.59</option>
        <option value="83.74">芬蘭/83.74</option>
        <option value="90.86">挪威/90.86</option>
        <option value="93.81">瑞士/93.81</option>
        <option value="125.56">瑞典/125.56</option>
        <option value="130.81">列支敦斯登/130.81</option>
        <option value="155.87">烏拉圭/155.87</option>
        <option value="55">美國/55</option>

        
        <!-- 可根据需要添加其他选项 -->
    </select>
    <input type="number" id="multiplier" placeholder="Enter multiplier">
    <button onclick="calculate()">Calculate</button>
    <p id="result"></p>

    <!-- 运算历史记录 -->
    <div id="history">
        <h3>Calculation History</h3>
        <ul id="historyList"></ul>
        <p id="totalResult">Total Result: 0</p>
    </div>

    <script>
        var totalResult = 0; // 用于累加结果
        var historyList = document.getElementById('historyList');
        var totalResultElement = document.getElementById('totalResult');

        function calculate() {
            var multiplicand = parseFloat(document.getElementById('multiplicand').value);
            var multiplier = parseFloat(document.getElementById('multiplier').value);
            var result;

            if (isNaN(multiplicand) || isNaN(multiplier)) {
                result = 'Invalid input';
            } else {
                result = multiplicand * multiplier;

                // 将结果添加到历史记录
                addToHistory(multiplicand, multiplier, result);

                // 累加结果
                totalResult += result;
                totalResultElement.innerHTML = 'Total Result: ' + roundToTwoDecimal(totalResult);
            }

            document.getElementById('result').innerHTML = 'Result: ' + roundToTwoDecimal(result);
        }

        function addToHistory(multiplicand, multiplier, result) {
            var historyItem = document.createElement('li');
            historyItem.textContent = multiplicand + ' * ' + multiplier + ' = ' + roundToTwoDecimal(result);
            historyList.appendChild(historyItem);
        }

        function roundToTwoDecimal(number) {
            return Math.round(number * 100) / 100;
        }
    </script>
</body>
</html>
