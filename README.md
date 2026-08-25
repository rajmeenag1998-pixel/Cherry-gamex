<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Cherry GameX</title>
<style>
body{margin:0;background:#080b14;color:#fff;font-family:Arial}
header{padding:18px;background:#111827;display:flex;justify-content:space-between}
.logo{color:#ff4757;font-size:24px;font-weight:bold}
.wallet{background:#1d2638;padding:10px;border-radius:10px}
main{max-width:700px;margin:30px auto;padding:15px}
.box{background:#111827;padding:25px;border-radius:18px;margin-bottom:20px}
button{padding:13px 18px;border:0;border-radius:9px;background:#ff4757;color:#fff;font-weight:bold;margin:5px}
.green{background:#19b983}
h1{text-align:center}
#coins{color:#ffd166}
</style>
</head>

<body>

<header>
<div class="logo">🍒 Cherry GameX</div>
<div class="wallet">
🪙 <span id="coins">10000</span> Coins
</div>
</header>

<main>

<div class="box">
<h1>Virtual Wallet</h1>

<p>Current Balance:
<b id="balance">10000</b> Virtual Coins
</p>

<button class="green" onclick="addCoins()">
➕ Add Demo Coins
</button>

<button onclick="bonus()">
🎁 Daily Demo Bonus
</button>

<p id="message"></p>
</div>

<div class="box">
<h2>🎮 Game Lobby</h2>
<button onclick="alert('Aviator Demo')">✈️ Aviator</button>
<button onclick="alert('Rummy Demo')">🃏 Rummy</button>
<button onclick="alert('Poker Demo')">♠️ Poker</button>
<button onclick="alert('Spin Demo')">🎰 Spin</button>
</div>

</main>

<script>
let coins=10000;
let bonusTaken=false;

function update(){
 document.getElementById("coins").textContent=coins.toLocaleString("en-IN");
 document.getElementById("balance").textContent=coins.toLocaleString("en-IN");
}

function addCoins(){
 coins+=1000;
 update();
 document.getElementById("message").textContent=
 "1000 demo coins add हुए 🎉";
}

function bonus(){
 if(bonusTaken){
   document.getElementById("message").textContent=
   "आज का demo bonus पहले ही लिया जा चुका है.";
   return;
 }

 coins+=500;
 bonusTaken=true;
 update();

 document.getElementById("message").textContent=
 "500 demo coins bonus मिले 🎁";
}

update();
</script>

</body>
</html>
