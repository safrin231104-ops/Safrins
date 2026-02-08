<!DOCTYPE html>
<html>
<head>
<title>Valentine 💜</title>
<style>
body{
  background: linear-gradient(to right,#e0c3fc,#8ec5fc);
  font-family: Arial;
  text-align:center;
  padding-top:60px;
  overflow:hidden;
}
.slide{ display:none; }
.active{ display:block; }

.box{
  background:white;
  padding:40px;
  border-radius:25px;
  display:inline-block;
  box-shadow:0 0 25px #c77dff;
}

button{
  padding:12px 25px;
  border:none;
  border-radius:12px;
  font-size:18px;
  margin:10px;
  cursor:pointer;
  background:#7b2cbf;
  color:white;
}

#result{
  font-size:28px;
  color:#7b2cbf;
  margin-top:15px;
}

#teddy{
  width:220px;
  display:none;
  animation:hug 0.8s infinite alternate;
}

@keyframes hug{
  from{ transform:scale(1) rotate(-5deg);}
  to{ transform:scale(1.15) rotate(5deg);}
}

.heart{
  position:fixed;
  top:-10px;
  animation: fall 6s linear infinite;
  z-index:999;
  pointer-events:none;
}
@keyframes fall{ to{ transform: translateY(100vh);} }
</style>
</head>

<body>

<!-- SLIDE 1 -->
<div id="slide1" class="slide active">
  <div class="box">
    <h1>Hello Dawood🤌🏻❤️‍🩹</h1>
    <h2>Will you be my Valentine? 💌</h2>
    <button onclick="yesClick()">YES</button>
    <button onclick="alert('Enga escape aaga pakurigaa broo 😼😹')">NO</button>

    <div id="result"></div>
    <img id="teddy" src="https://media.tenor.com/9sFQJjK7X8UAAAAi/bear-hug.gif">
  </div>
</div>

<!-- SLIDE 2 PASSWORD -->
<div id="slide2" class="slide">
  <div class="box">
    <h2>Extra Love Slide 🔐</h2>
    <p>Password enter pannunga</p>
    <p><b>Hint:</b> love you pondatti 💜</p>
    <input id="pass" placeholder="Enter password">
    <br><br>
    <button onclick="checkPass()">Open</button>
  </div>
</div>

<!-- SLIDE 3 MESSAGE -->
<div id="slide3" class="slide">
  <div class="box">
    <h2 id="typing"></h2>
  </div>
</div>

<script>
function yesClick(){
  document.getElementById("result").innerHTML="Awww🥹🫶🏻😩 Love you pattaniii 🥹🫂💋";
  document.getElementById("teddy").style.display="block";
  startHearts();
  setTimeout(()=>switchSlide(2),3000);
}

function switchSlide(n){
  document.querySelectorAll(".slide").forEach(s=>s.classList.remove("active"));
  document.getElementById("slide"+n).classList.add("active");
}

function checkPass(){
  let p=document.getElementById("pass").value.toLowerCase().trim();
  if(p=="love you pondatti"){
    switchSlide(3);
    startTyping();
  }else alert("Wrong password brooo😼🫡");
}

function startTyping(){
  document.getElementById("typing").innerHTML="";
  let msg=`Inga paaru daa… ennaku unna matum dha romba pudikum…
Naa unna dha neraiya luv panren… engaiyum enna vitutu pogadhe… nanum poga maten 🥹🫂

Miss you ❤️‍🩹
Love you moreeeeee daaaa myluuuuuu 🫂💋💋`;

  let i=0;
  function type(){
    if(i < msg.length){
      document.getElementById("typing").innerHTML += 
        msg.charAt(i) === "\n" ? "<br>" : msg.charAt(i);
      i++;
      setTimeout(type,40);
    }
  }
  type();
}

function startHearts(){
  setInterval(function(){
    var heart=document.createElement("div");
    heart.className="heart";
    var colors=["💜","💙"];
    heart.innerHTML=colors[Math.floor(Math.random()*colors.length)];
    heart.style.left=Math.random()*100+"vw";
    heart.style.fontSize=(Math.random()*20+18)+"px";
    document.body.appendChild(heart);
  },700);
}
</script>

</body>
</html>
