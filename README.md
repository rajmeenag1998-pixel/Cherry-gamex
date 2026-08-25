<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cherry GameX</title>
<style>
body{
  margin:0;
  font-family:Arial,sans-serif;
  background:#080b14;
  color:white;
}
header{
  padding:20px;
  text-align:center;
  background:#111827;
  border-bottom:1px solid #252d40;
}
.logo{
  font-size:30px;
  font-weight:bold;
  color:#ff4757;
}
.hero{
  text-align:center;
  padding:60px 20px;
}
.hero h1{
  font-size:42px;
  margin:10px;
}
.hero p{
  color:#aab3c5;
}
.btn{
  display:inline-block;
  padding:14px 28px;
  background:#ff4757;
  color:white;
  border-radius:10px;
  text-decoration:none;
  font-weight:bold;
}
.games{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
  gap:15px;
  padding:25px;
  max-width:900px;
  margin:auto;
}
.game{
  background:#151c2c;
  padding:25px 15px;
  border-radius:15px;
  text-align:center;
  border:1px solid #252d40;
}
.icon{
  font-size:40px;
}
</style>
</head>

<body>

<header>
  <div class="logo">🍒 Cherry GameX</div>
</header>

<section class="hero">
  <h1>Welcome to Cherry GameX</h1>
  <p>Multi Gaming • Virtual Points • Fun</p>
  <a class="btn" href="#games">गेम्स देखें</a>
</section>

<section class="games" id="games">

  <div class="game">
    <div class="icon">✈️</div>
    <h3>Aviator Demo</h3>
    <p>Virtual Points</p>
  </div>

  <div class="game">
    <div class="icon">🍒</div>
    <h3>Cherry</h3>
    <p>Virtual Points</p>
  </div>

  <div class="game">
    <div class="icon">🃏</div>
    <h3>Cards Demo</h3>
    <p>Virtual Points</p>
  </div>

  <div class="game">
    <div class="icon">🍭</div>
    <h3>Fruit Game</h3>
    <p>Virtual Points</p>
  </div>

</section>

</body>
</html>
