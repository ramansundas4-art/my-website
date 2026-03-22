# my-website
Personal HTML website project
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For You ❤️</title>

<style>
body {
    margin: 0;
    overflow: hidden;
    font-family: Arial, sans-serif;
    text-align: center;
    color: white;
    background: linear-gradient(270deg,#ff758c,#ff7eb3,#ff4d6d);
    background-size: 600% 600%;
    animation: bgMove 10s infinite;
}

/* background animation */
@keyframes bgMove {
    0% {background-position:0%}
    50% {background-position:100%}
    100% {background-position:0%}
}

/* 💖 TOP NAME */
#name {
    position: absolute;
    top: 20px;
    width: 100%;
    font-size: 45px;
    font-weight: bold;
    text-align: center;
    text-shadow: 0 0 10px white, 0 0 20px pink;
    animation: glow 2s infinite alternate;
}

@keyframes glow {
    0% {text-shadow:0 0 10px white,0 0 20px pink;}
    100% {text-shadow:0 0 20px white,0 0 40px hotpink;}
}

.container {
    position: relative;
    top: 120px;
}

h1 {
    font-size: 30px;
}

#text {
    font-size: 22px;
    min-height: 60px;
    margin: 20px;
}

/* buttons */
button {
    padding: 12px 25px;
    font-size: 18px;
    border: none;
    border-radius: 25px;
    cursor: pointer;
    margin: 10px;
}

.yes { background: #00ff99; }
.no { background: #ff4d4d; color: white; }

/* 💍 ring */
#ring {
    font-size: 90px;
    display: none;
    animation: ringPop 1.2s ease infinite alternate;
    filter: drop-shadow(0 0 10px white);
}

@keyframes ringPop {
    0% { transform: scale(0.9) translateY(0px); }
    100% { transform: scale(1.1) translateY(-10px); }
}

/* hearts */
.heart {
    position: absolute;
    font-size: 20px;
    animation: float 6s linear infinite;
}

@keyframes float {
    0% {transform: translateY(100vh); opacity:1;}
    100% {transform: translateY(-10vh); opacity:0;}
}

/* message box */
.msgBox {
    background: white;
    color: black;
    padding: 12px;
    border-radius: 10px;
    display: inline-block;
}
</style>
</head>

<body>

<!-- 💖 NAME -->
<div id="name">Raman ❤️</div>

<div class="container">

    <h1>Something for you 💖</h1>

    <div id="text"></div>

    <!-- 💍 Ring -->
    <div id="ring">💍</div>

    <button onclick="nextStep()">Click 💕</button>

    <div id="buttons" style="display:none;">
        <button class="yes" onclick="yesLove()">Yes 💖</button>
        <button class="no" onclick="noLove()">No 😅</button>
    </div>

    <p id="final"></p>
</div>

<script>

let step = 0;

function typeText(msg, i=0){
    let el = document.getElementById("text");

    if(i === 0) el.innerHTML = "";

    if(i < msg.length){
        el.innerHTML += msg.charAt(i);
        setTimeout(()=>typeText(msg,i+1),40);
    }
}

function nextStep(){
    step++;

    if(step===1){
        typeText("I have something special for you 😊");
    }
    else if(step===2){
        typeText("You always stay in my heart 💭");
    }
    else if(step===3){
        typeText("You make everything better ❤️");
    }
    else if(step===4){
        typeText("Will you be my partner? 💕");

        document.getElementById("buttons").style.display="block";
        document.getElementById("ring").style.display="block";

        createHearts();
    }
}

/* YES */
function yesLove(){

    document.getElementById("final").innerHTML = `
        💬 Send this in DM ❤️<br><br>

        <div class="msgBox">
            YES 💖 I accept you 😍
        </div>

        <br><br>

        <button onclick="copyText('YES 💖 I accept you 😍')" style="background:#00ff99;">
            📋 Copy Message
        </button>
    `;

    createHearts();
}

/* NO */
function noLove(){

    document.getElementById("final").innerHTML = `
        💬 Reply in DM ❤️<br><br>

        <div class="msgBox">
            NO 😅 I need more time ❤️
        </div>

        <br><br>

        <button onclick="copyText('NO 😅 I need more time ❤️')" style="background:#ff4d4d;">
            📋 Copy Message
        </button>
    `;

    createHearts();
}

/* COPY */
function copyText(text){
    navigator.clipboard.writeText(text);
    alert("Copied ❤️");
}

/* HEARTS */
function createHearts(){
    setInterval(()=>{
        let h=document.createElement("div");
        h.className="heart";
        h.innerHTML="❤️";
        h.style.left=Math.random()*100+"vw";
        document.body.appendChild(h);
        setTimeout(()=>h.remove(),6000);
    },300);
}

</script>

</body>
</html>
