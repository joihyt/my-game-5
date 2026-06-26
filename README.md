<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<title>🎮 猜數字挑戰</title>

<style>
body {
  font-family: Arial;
  text-align: center;
  background: linear-gradient(135deg, #74ebd5, #ACB6E5);
  color: #333;
}

.container {
  margin-top: 100px;
  background: white;
  display: inline-block;
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 0 20px rgba(0,0,0,0.2);
}

input {
  padding: 10px;
  font-size: 18px;
  width: 100px;
}

button {
  padding: 10px 15px;
  font-size: 16px;
  margin-top: 10px;
  cursor: pointer;
}

#result {
  margin-top: 15px;
  font-size: 18px;
  font-weight: bold;
}

#timer {
  color: red;
  font-size: 20px;
}
</style>
</head>

<body onload="startGame()">

<div class="container">
  <h2>🎮 猜數字挑戰</h2>
  <p>猜一個 1 ~ 50 的數字</p>
  <p>⏱️ 剩餘時間：<span id="timer">10</span> 秒</p>

  <input id="guess" type="number">
  <br>
  <button onclick="check()">猜！</button>
  <br>
  <button onclick="startGame()">重新開始</button>

  <p id="result"></p>
</div>

<script>
let answer;
let time;
let countdown;

function startGame() {
  answer = Math.floor(Math.random() * 50) + 1;
  time = 10;
  document.getElementById("timer").innerText = time;
  document.getElementById("result").innerText = "";
  document.getElementById("guess").value = "";

  clearInterval(countdown);

  countdown = setInterval(() => {
    time--;
    document.getElementById("timer").innerText = time;

    if (time <= 0) {
      clearInterval(countdown);
      document.getElementById("result").innerText =
        "💀 時間到！答案是 " + answer;
    }
  }, 1000);
}

function check() {
  let guess = document.getElementById("guess").value;

  if (time <= 0) return;

  if (guess == answer) {
    document.getElementById("result").innerText = "🎉 猜對了！";
    clearInterval(countdown);
  } else if (guess > answer) {
    document.getElementById("result").innerText = "📉 太大了！";
  } else {
    document.getElementById("result").innerText = "📈 太小了！";
  }
}
</script>

</body>
</html>
