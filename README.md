<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>A Valentine Moment 💖</title>

<style>
body{
  margin:0;
  height:100vh;
  background:linear-gradient(135deg,#ff9a9e,#fad0c4);
  display:flex;
  justify-content:center;
  align-items:center;
  font-family:"Georgia", serif;
  overflow:hidden;
  text-align:center;
  color:#fff;
}

.container{
  z-index:5;
  padding:40px;
}

h1{
  font-size:38px;
  margin-bottom:20px;
}

p{
  font-size:20px;
  line-height:1.6;
}

button{
  padding:12px 28px;
  margin:15px;
  font-size:18px;
  border:none;
  border-radius:30px;
  cursor:pointer;
}

#yes{
  background:#ff4b6e;
  color:white;
}

#no{
  background:#fff;
  color:#ff4b6e;
  position:absolute;
}

/* 💖 Fancy text animation */
#msg{
  font-size:34px;
  line-height:1.5;
  animation:fadeZoom 4s ease-in-out infinite;
}

@keyframes fadeZoom{
  0%{opacity:0;transform:scale(0.95);}
  20%{opacity:1;transform:scale(1);}
  80%{opacity:1;}
  100%{opacity:0;transform:scale(1.05);}
}

/* ❤️ Hearts */
.heart{
  position:fixed;
  top:-10px;
  font-size:22px;
  animation:fall linear forwards;
}

@keyframes fall{
  to{transform:translateY(110vh);opacity:0;}
}

/* 🎈 Balloons */
.balloon{
  position:fixed;
  bottom:-40px;
  font-size:30px;
  animation:floatUp linear forwards;
}

@keyframes floatUp{
  to{transform:translateY(-120vh);opacity:0;}
}

/* ✨ Sparkles */
.sparkle{
  position:fixed;
  width:6px;
  height:6px;
  background:white;
  border-radius:50%;
  box-shadow:0 0 12px gold;
  animation:sparkle 1.5s linear forwards;
}

@keyframes sparkle{
  to{transform:translateY(-40px);opacity:0;}
}

/* 🧸 Floating teddies */
.teddy{
  position:fixed;
  bottom:-40px;
  font-size:32px;
  animation:teddyFloat linear forwards;
}

@keyframes teddyFloat{
  to{transform:translateY(-120vh) rotate(-10deg);opacity:0;}
}

/* 🧸❤️ BIG TEDDY */
.big-teddy{
  font-size:120px;
  margin-bottom:20px;
  animation:hug 3s ease-in-out infinite;
}

@keyframes hug{
  0%,100%{transform:scale(1);}
  50%{transform:scale(1.05);}
}

/* 🌸 Petals */
.petal{
  position:fixed;
  top:-10px;
  font-size:20px;
  animation:petalFall linear forwards;
}

@keyframes petalFall{
  to{transform:translateY(110vh) rotate(360deg);opacity:0;}
}
</style>
</head>

<body>

<div class="container" id="start">
  <h1>Paresh 🌸</h1>
  <p>
    Some feelings feel warmer,<br>
    some moments feel softer…<br><br>
    Will you be my Valentine? 💕
  </p>

  <button id="yes" onclick="yesAccepted()">Yes 💖</button>
  <button id="no" onmouseover="moveNo()">No</button>
</div>

<script>
const noTexts=[
  "Think again 💭",
  "My heart says yes 💘",
  "This doesn’t feel right 😜",
  "Only love fits here ✨"
];

function moveNo(){
  const n=document.getElementById("no");
  n.innerText=noTexts[Math.floor(Math.random()*noTexts.length)];
  n.style.left=Math.random()*(window.innerWidth-120)+"px";
  n.style.top=Math.random()*(window.innerHeight-60)+"px";
}

function yesAccepted(){
  document.body.innerHTML=`
    <div class="container">
      <h1 id="msg"></h1>
    </div>
  `;

  const messages=[
    "She said YES 💖<br>Always grateful to have you ✨",
    "Riya 🌸<br>You’re my daily happiness 💫",
    "You’re my constant happiness 💕",
    "This moment…<br>I’ll keep it close 💘"
  ];

  let i=0;
  const msg=document.getElementById("msg");
  msg.innerHTML=messages[0];

  const loop=setInterval(()=>{
    i++;
    if(i<messages.length){
      msg.innerHTML=messages[i];
    }else{
      clearInterval(loop);
      endScene();
    }
  },4000);

  setInterval(createHeart,450);
  setInterval(createBalloon,1200);
  setInterval(createSparkle,350);
  setInterval(createTeddy,2000);
}

function endScene(){
  document.body.style.background="linear-gradient(135deg,#2b5876,#4e4376)";
  document.body.innerHTML=`
    <div class="container">
      <div class="big-teddy">🧸❤️</div>
      <h1 style="animation:none;font-size:32px;">
        This teddy carries my heart<br>
        straight to you 💖<br><br>
        Thank you for being in my life 🌙<br><br>
        <span style="font-size:22px;">— Sahil</span>
      </h1>
    </div>
  `;

  setInterval(createPetal,900);
}

function createHeart(){
  const h=document.createElement("div");
  h.className="heart";
  h.innerText="❤️";
  h.style.left=Math.random()*100+"vw";
  h.style.animationDuration=(3+Math.random()*3)+"s";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),6000);
}

function createBalloon(){
  const b=document.createElement("div");
  b.className="balloon";
  b.innerText="🎈";
  b.style.left=Math.random()*100+"vw";
  b.style.animationDuration=(5+Math.random()*4)+"s";
  document.body.appendChild(b);
  setTimeout(()=>b.remove(),9000);
}

function createSparkle(){
  const s=document.createElement("div");
  s.className="sparkle";
  s.style.left=Math.random()*100+"vw";
  s.style.top=Math.random()*100+"vh";
  document.body.appendChild(s);
  setTimeout(()=>s.remove(),1500);
}

function createTeddy(){
  const t=document.createElement("div");
  t.className="teddy";
  t.innerText="🧸";
  t.style.left=Math.random()*100+"vw";
  t.style.animationDuration=(6+Math.random()*4)+"s";
  document.body.appendChild(t);
  setTimeout(()=>t.remove(),10000);
}

function createPetal(){
  const p=document.createElement("div");
  p.className="petal";
  p.innerText="🌸";
  p.style.left=Math.random()*100+"vw";
  p.style.animationDuration=(6+Math.random()*4)+"s";
  document.body.appendChild(p);
  setTimeout(()=>p.remove(),10000);
}
</script>

</body>
</html># Will-you-be-my-valentine-
Html code
