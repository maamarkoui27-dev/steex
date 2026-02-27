<!DOCTYPE html>
<html>
<head>
  <title>عداد تنازلي دائري ملون</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      height: 100vh;
      background: linear-gradient(135deg, #6a11cb, #2575fc);
      font-family: 'Arial', sans-serif;
      margin: 0;
      color: #fff;
    }
    h1 {
      margin-bottom: 40px;
      text-shadow: 2px 2px 8px rgba(0,0,0,0.3);
      font-size: 2em;
    }
    .circles {
      display: flex;
      gap: 15px;
      flex-wrap: wrap;
      justify-content: center;
    }
    .circle {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      font-size: 1.2em;
      text-align: center;
      box-shadow: 0 4px 10px rgba(0,0,0,0.3);
      transition: transform 0.3s, background 0.3s;
    }
    .circle:hover {
      transform: scale(1.1);
    }
    .number {
      font-size: 1.5em;
      font-weight: bold;
    }
    .label {
      margin-top: 5px;
      font-size: 0.9em;
    }
    .years { background: #ff6b6b; }
    .months { background: #feca57; }
    .days { background: #54a0ff; }
    .hours { background: #1dd1a1; }
    .minutes { background: #5f27cd; }
    .seconds { background: #ff9ff3; }
  </style>
</head>
<body>
  <h1>الوقت المتبقي حتى 27/06/2029</h1>
  <div class="circles">
    <div class="circle years"><div class="number" id="years">0</div><div class="label">سنوات</div></div>
    <div class="circle months"><div class="number" id="months">0</div><div class="label">شهور</div></div>
    <div class="circle days"><div class="number" id="days">0</div><div class="label">أيام</div></div>
    <div class="circle hours"><div class="number" id="hours">0</div><div class="label">ساعات</div></div>
    <div class="circle minutes"><div class="number" id="minutes">0</div><div class="label">دقائق</div></div>
    <div class="circle seconds"><div class="number" id="seconds">0</div><div class="label">ثواني</div></div>
  </div>

  <script>
    const targetDate = new Date("2029-06-27T00:00:00").getTime();

    function updateCountdown() {
      const now = new Date().getTime();
      const diff = targetDate - now;

      if(diff <= 0){
        document.querySelectorAll('.number').forEach(n => n.innerText = 0);
        return;
      }

      const years = Math.floor(diff / (1000*60*60*24*365));
      const months = Math.floor((diff % (1000*60*60*24*365)) / (1000*60*60*24*30));
      const days = Math.floor((diff % (1000*60*60*24*30)) / (1000*60*60*24));
      const hours = Math.floor((diff % (1000*60*60*24)) / (1000*60*60));
      const minutes = Math.floor((diff % (1000*60*60)) / (1000*60));
      const seconds = Math.floor((diff % (1000*60)) / 1000);

      document.getElementById("years").innerText = years;
      document.getElementById("months").innerText = months;
      document.getElementById("days").innerText = days;
      document.getElementById("hours").innerText = hours;
      document.getElementById("minutes").innerText = minutes;
      document.getElementById("seconds").innerText = seconds;
    }

    setInterval(updateCountdown, 1000);
    updateCountdown();
  </script>
</body>
</html>