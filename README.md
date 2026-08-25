<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Cherry GameX</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:#080b14;color:#fff;font-family:Arial,sans-serif}
header{padding:18px;background:#111827;display:flex;justify-content:space-between;align-items:center}
.logo{font-size:24px;font-weight:800;color:#ff4757}
.balance{background:#1b2435;padding:10px 15px;border-radius:10px}
nav{display:flex;gap:8px;padding:12px;overflow:auto;background:#0d1320}
nav button{white-space:nowrap;background:#1b2435;color:#fff;border:0;padding:11px 16px;border-radius:9px}
main{max-width:900px;margin:auto;padding:15px}
.game{background:#111827;border:1px solid #273149;border-radius:18px;padding:20px;min-height:430px}
h1{text-align:center}
.screen{text-align:center;background:#080d18;border-radius:15px;padding:55px 15px;margin:15px 0}
.big{font-size:60px;font-weight:900;color:#ff5262}
input,button{padding:13px;border:0;border-radius:9px}
input{background:#20293a;color:#fff;width:150px}
.play{background:#ff4757;color:#fff;font-weight:bold}
.green{background:#19b983;color:#fff;font-weight:bold}
.cards{display:flex;justify-content:center;gap:8px;flex-wrap:wrap;margin:25px}
.card{background:#fff;color:#111;padding:22px 16px;border-radius:9px;font-size:25px;min-width:60px}
.msg{text-align:center;color:#ffd166;min-height:25px}
</style>
</head>
<body>

<header>
<div class="logo">🍒 Cherry GameX</div>
<div class="balance">Points: <b id="bal">10000</b></div>
</header>

<nav>
<button onclick="show('aviator')">✈️ Aviator</button>
<button onclick="show('rummy')">🃏 Rummy</button>
<button onclick="show('poker')">♠️ Poker</button>
<button onclick="show('spin')">🎰 Spin</button>
</nav>

<main>

<section id="aviator" class="game">
<h1>✈️ Aviator Demo</h1>
<div class="screen">
<div id="multi" class="big">1.00x</div>
<div>Virtual Points Demo</div>
</div>
<div style="text-align:center">
<input id="aviBet" type="number" value="100" min="10">
<button class="play" id="aviPlay" onclick="aviator()">START</button>
<button class="green" id="cash" onclick="cashout()" disabled>CLAIM</button>
</div>
<p class="msg" id="aviMsg"></p>
</section>

<section id="rummy" class="game" style="display:none">
<h1>🃏 Rummy Demo</h1>
<div class="cards" id="rCards"></div>
<div style="text-align:center">
<button class="play" onclick="rummy()">DRAW CARDS</button>
</div>
<p class="msg" id="rMsg"></p>
</section>

<section id="poker" class="game" style="display:none">
<h1>♠️ Poker Demo</h1>
<div class="cards" id="pCards"></div>
<div style="text-align:center">
<button class="play" onclick="poker()">DEAL HAND</button>
</div>
<p class="msg" id="pMsg"></p>
</section>

<section id="spin" class="game" style="display:none">
<h1>🎰 Spin Demo</h1>
<div class="screen">
<div id="slots" class="big">🍒 | ⭐ | 7️⃣</div>
</div>
<div style="text-align:center">
<button class="play" onclick="spin()">SPIN</button>
</div>
<p class="msg" id="sMsg"></p>
</section>

</main>

<script>
let balance=10000;
let running=false,cur=1,bet=0,timer;

const $=x=>document.getElementById(x);
function sync(){$("bal").textContent=balance.toLocaleString("en-IN")}

function show(id){
 document.querySelectorAll(".game").forEach(x=>x.style.display="none");
 $(id).style.display="block";
}

function aviator(){
 if(running)return;
 bet=+$("aviBet").value;
 if(bet<10||bet>balance){
   $("aviMsg").textContent="Valid virtual points डालें";
   return;
 }
 balance-=bet;sync();
 running=true;cur=1;
 $("aviPlay").disabled=true;
 $("cash").disabled=false;
 $("aviMsg").textContent="Multiplier बढ़ रहा है…";

 let crash=+(1.2+Math.random()*6).toFixed(2);

 timer=setInterval(()=>{
   cur+=.06;
   $("multi").textContent=cur.toFixed(2)+"x";
   if(cur>=crash){
     clearInterval(timer);
     running=false;
     $("cash").disabled=true;
     $("aviPlay").disabled=false;
     $("aviMsg").textContent="Round खत्म: "+crash.toFixed(2)+"x";
   }
 },80);
}

function cashout(){
 if(!running)return;
 clearInterval(timer);
 let win=Math.floor(bet*cur);
 balance+=win;
 sync();
 running=false;
 $("cash").disabled=true;
 $("aviPlay").disabled=false;
 $("aviMsg").textContent="Claim: "+win+" virtual points";
}

const suits=["♠","♥","♦","♣"];
const ranks=["A","2","3","4","5","6","7","8","9","10","J","Q","K"];

function randomCard(){
 return ranks[Math.floor(Math.random()*ranks.length)] +
        suits[Math.floor(Math.random()*suits.length)];
}

function rummy(){
 $("rCards").innerHTML="";
 for(let i=0;i<7;i++){
   let d=document.createElement("div");
   d.className="card";
   d.textContent=randomCard();
   $("rCards").appendChild(d);
 }
 $("rMsg").textContent="7 virtual cards dealt.";
}

function poker(){
 $("pCards").innerHTML="";
 for(let i=0;i<5;i++){
   let d=document.createElement("div");
   d.className="card";
   d.textContent=randomCard();
   $("pCards").appendChild(d);
 }
 $("pMsg").textContent="5-card demo hand dealt.";
}

function spin(){
 const symbols=["🍒","🍋","⭐","💎","7️⃣"];
 let a=symbols[Math.floor(Math.random()*symbols.length)];
 let b=symbols[Math.floor(Math.random()*symbols.length)];
 let c=symbols[Math.floor(Math.random()*symbols.length)];
 $("slots").textContent=a+" | "+b+" | "+c;

 if(a===b&&b===c){
   balance+=500;sync();
   $("sMsg").textContent="+500 virtual points 🎉";
 }else{
   $("sMsg").textContent="Try again!";
 }
}
sync();
</script>

</body>
</html>
