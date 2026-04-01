<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ultra Pink Love</title>

<style>
body {
  margin: 0;
  height: 100vh;
  overflow: hidden;
  background: linear-gradient(135deg, #ff9a9e, #ff69b4, #ffb6c1);
  background-size: 400% 400%;
  animation: bgMove 10s ease infinite;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Arial;
}

@keyframes bgMove {
  0% {background-position: 0% 50%;}
  50% {background-position: 100% 50%;}
  100% {background-position: 0% 50%;}
}

/* الكارد */
.card {
  text-align: center;
  padding: 40px;
  border-radius: 25px;
  background: rgba(255,255,255,0.2);
  backdrop-filter: blur(20px);
  box-shadow: 0 0 60px rgba(0,0,0,0.3);
  animation: float 4s ease-in-out infinite;
}

@keyframes float {
  0%,100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

/* القط */
#kitty {
  font-size: 140px;
  transition: 0.5s;
  text-shadow: 0 0 20px white;
}

/* النص */
h1 {
  color: white;
  text-shadow: 0 0 15px white;
}

/* الأزرار */
button {
  padding: 14px 35px;
  margin: 10px;
  border: none;
  border-radius: 12px;
  font-size: 18px;
  cursor: pointer;
  transition: 0.3s;
}

#yes {
  background: linear-gradient(45deg, #ff2e63, #ff6b81);
  color: white;
}

#no {
  background: #222;
  color: white;
}

button:hover {
  transform: scale(1.2);
}

/* القلوب */
.heart {
  position: absolute;
  font-size: 22px;
  animation: fall 5s linear infinite;
  filter: drop-shadow(0 0 5px white);
}

@keyframes fall {
  from { transform: translateY(-10vh) rotate(0deg); }
  to { transform: translateY(110vh) rotate(360deg); }
}

/* انفجار */
.explode {
  position: absolute;
  font-size: 26px;
  animation: boom 1s forwards;
}

@keyframes boom {
  0% { transform: scale(1); opacity: 1; }
  100% { transform: scale(5) translateY(-200px); opacity: 0; }
}
</style>
</head>

<body>

<div class="card">
  <h1 id="question">تحبنييييييي ؟؟ 🌸</h1>
  <div id="kitty">😿</div>

  <button id="yes">نعم 💖</button>
  <button id="no">لا 💔</button>
</div>

<script>

const hearts = ["💗","💖","💕"];

/* قلوب متساقطة */
setInterval(() => {
  let h = document.createElement("div");
  h.className = "heart";
  h.innerHTML = hearts[Math.floor(Math.random()*hearts.length)];

  h.style.left = Math.random()*100 + "vw";
  h.style.animationDuration = (3 + Math.random()*3) + "s";

  document.body.appendChild(h);

  setTimeout(() => h.remove(), 7000);
}, 150);

/* YES */
document.getElementById("yes").onclick = () => {

  document.getElementById("question").innerText = "😻💖 شكرااااا!";
  document.getElementById("kitty").innerText = "😽💫💗💖";

  // انفجار قوي
  for(let i=0;i<120;i++){
    let e = document.createElement("div");
    e.className = "explode";
    e.innerHTML = hearts[Math.floor(Math.random()*hearts.length)];

    e.style.left = Math.random()*100 + "vw";
    e.style.top = "50vh";

    document.body.appendChild(e);
    setTimeout(() => e.remove(), 1000);
  }
};

/* NO */
document.getElementById("no").onclick = (e) => {

  document.getElementById("question").innerText = "😿💔 حزييينة...";

  let btn = e.target;
  btn.style.position = "absolute";

  btn.style.left = Math.random() * (window.innerWidth - 100) + "px";
  btn.style.top = Math.random() * (window.innerHeight - 100) + "px";
};

</script>

</body>
</html>
