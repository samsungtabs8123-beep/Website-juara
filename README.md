# Website-juara
Kemenangan juara spaceflight simulator
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Juara 1 🎉</title>

<style>
body {
  margin:0;
  font-family: Arial;
  background:black;
  color:white;
  text-align:center;
  overflow:hidden;
}

/* LOADING */
#loading {
  position:fixed;
  width:100%;
  height:100%;
  background:black;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:30px;
  z-index:10;
}

/* KONTEN */
.container {
  display:none;
  padding:20px;
}

h1 {
  font-size:50px;
  color:gold;
  animation: glow 1s infinite alternate;
}

@keyframes glow {
  from { text-shadow:0 0 10px gold; }
  to { text-shadow:0 0 30px yellow; }
}

img {
  width:80%;
  border-radius:20px;
  animation: zoom 2s infinite alternate;
}

@keyframes zoom {
  from { transform:scale(1); }
  to { transform:scale(1.05); }
}

.hadiah {
  font-size:30px;
  color:#00ffcc;
  margin:15px;
}

/* TYPE TEXT */
#typing {
  font-size:20px;
  width:80%;
  margin:auto;
  border-right:2px solid white;
  white-space:nowrap;
  overflow:hidden;
}

/* CONFETTI */
canvas {
  position:fixed;
  top:0;
  left:0;
  pointer-events:none;
}
</style>
</head>

<body>

<div id="loading">Loading...</div>

<canvas id="confetti"></canvas>

<div class="container" id="main">
  <h1>🏆 JUARA 1 🏆</h1>
  <img src="rocket.jpg">
  <div class="hadiah">🎉 Mendapatkan 100 Juta 🎉</div>
  <p id="typing"></p>
</div>

<script>
/* LOADING EFFECT */
setTimeout(()=>{
  document.getElementById('loading').style.display='none';
  document.getElementById('main').style.display='block';
  startTyping();
},2000);

/* TYPING EFFECT */
const text = "Selamat! Kamu berhasil menjadi juara pertama dengan usaha luar biasa. Hadiah 100 juta ini adalah bukti kerja kerasmu!";
let i = 0;

function startTyping(){
  let speed = setInterval(()=>{
    if(i < text.length){
      document.getElementById("typing").innerHTML += text.charAt(i);
      i++;
    } else {
      clearInterval(speed);
    }
  },50);
}

/* CONFETTI */
const canvas = document.getElementById('confetti');
const ctx = canvas.getContext('2d');

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const pieces = [];

for(let i=0;i<120;i++){
  pieces.push({
    x: Math.random()*canvas.width,
    y: Math.random()*canvas.height,
    size: Math.random()*6+2,
    speed: Math.random()*3+1
  });
}

function update(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  pieces.forEach(p=>{
    p.y += p.speed;
    if(p.y > canvas.height) p.y = 0;

    ctx.fillStyle = `hsl(${Math.random()*360},100%,50%)`;
    ctx.fillRect(p.x,p.y,p.size,p.size);
  });
  requestAnimationFrame(update);
}

update();
</script>

</body>
</html>
