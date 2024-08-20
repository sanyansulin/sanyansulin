<!DOCTYPE html>
<html lang="pt">

<head>
  <!-- Font Sacramento -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Sacramento&display=swap" rel="stylesheet">

  <!-- Font Montserrat Alternates -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat+Alternates:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet">

  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Saudações Widget</title>

  <style>
    /* CSS RESETS */
    body {
      background-color: #fff;
      line-height: 1.6;
    }

    h1 {
      margin-top: 0;
    }

    /* CSS START */
    .full-table {
      display: table;
      height: 100%;
      width: 100%;
    }

    .table-cell {
      display: table-cell;
      vertical-align: middle;
      text-align: center;
    }

    .card {
      padding: 10px 25px;
      border-radius: 10px;
      background: #000;
      width: 80vw;
      color: #fff;
      display: inline-block;
      box-shadow: 2px 2px 1px 0px #330835;
    }

    .card:hover {
      margin-top: 2px;
      box-shadow: none;
    }

    .clock {
      display: inline;
      font-family: 'Montserrat Alternates', sans-serif;
      font-size: 1.5em; /* Ajustado para um tamanho menor */
    }

    .time {
      display: inline;
      min-width: 37px;
    }

    .colon {
      font-size: 1.1em;
      display: inline-block;
    }

    .date {
      display: inline;
      min-width: 250px;
      font-family: 'Montserrat Alternates', sans-serif;
      font-size: 1.5em; /* Ajustado para um tamanho menor */
      padding-right: 60px;
    }

    .greet {
      display: inline;
      font-family: 'Sacramento', cursive;
      font-size: 3rem;
      padding-right: 60px;
    }
  </style>
</head>

<body>
  <div class="full-table">
    <div class="table-cell">

      <div class="card">
        <div class="greet" id="greet"></div>
        <div class="date" id="date"></div>
        <div class="clock">
          <div class="time" id="hour"></div>
          <div class="colon">:</div>
          <div class="time" id="min"></div>
          <div class="colon">:</div>
          <div class="time" id="sec"></div>
        </div>
      </div>

    </div>
  </div>

  <script>
    function formatDate() {
      var today = new Date();
      var options = { weekday: 'long', day: 'numeric', month: 'long', year: 'numeric' };
      document.getElementById('date').innerHTML = today.toLocaleDateString('pt-BR', options);
    }

    function clock() {
      var today = new Date();
      var hour = zeros(today.getHours());
      var minutes = zeros(today.getMinutes());
      var seconds = zeros(today.getSeconds());
      var greet;

      if (today.getHours() >= 6 && today.getHours() < 12) {
        greet = 'Bom Dia, Sany';
      } else if (today.getHours() >= 12 && today.getHours() < 18) {
        greet = 'Boa Tarde, Sany';
      } else {
        greet = 'Boa Noite, Sany';
      }

      document.getElementById('greet').innerHTML = greet;
      document.getElementById('hour').innerHTML = hour;
      document.getElementById('min').innerHTML = minutes;
      document.getElementById('sec').innerHTML = seconds;
    }

    function zeros(num) {
      return num < 10 ? '0' + num : num;
    }

    function dateTime() {
      formatDate();
      clock();
      setTimeout(dateTime, 1000);
    }

    dateTime();
  </script>

</body>

</html>
