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
