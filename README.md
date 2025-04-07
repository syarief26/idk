<!DOCTYPE html>
<html lang="en">

<head>
  <title>WishU</title>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="style.css">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css" />
</head>

<body>
  <div class="container">
    <div id="one" class="one">
      <h1>Hey
        <span id="name" class="name animate__delay-1s">Ayu Maulida Utami</span>
      </h1>
      <p class="two animate__delay-2s" id="greetingText">It's your birthday!!! :D</p>
    </div>
    <div class="three animate__delay-5s">
      I wanted to do something special, so I made this for you :)
    </div>
    <div class="wish" id="balloon-container">
      <img src="assets/01152 Happy Birthday.svg" class="wish-hbd animate__delay-5s center" alt="happy birthday">
      <br><br>
      <h5 class="wishText animate__delay-5s"><span id="wishText">There is no need for a special day to remind me how special you are and how
        important you are. The stars shine wherever you go.</span><br><span id="gradient-text">Happy 17<span
            id="seconds"></span><sup>nd</sup> Birthday</span> ;)</h5>
    </div>
    <div class="buttons">
      <a type="button" href="https://www.youtube.com/watch?v=k3zimSRKqNw" title="Follow you">
        <span class="heart animate__delay-5s"><span>Made with </span><img
            class="heart-icon animate__delay-5s" src="assets/icons8-diamond-heart-48.png"
            style="width: 18px;height: 15px;" alt="3" title="Hey D, :)"> by <span id="heartText">Architrixs</span></span>
      </a>
      <a type="button" class="refresh-btn animate__delay-5s" onClick="refreshPage()"><img
          src="assets/icons8-refresh-30.png" style="width: 23px;height: 23px;" alt="Refresh" title="Refresh"></a>
    </div>
  </div>
</body>
<script type="application/javascript" src="main.js"></script>

</html>
<!DOCTYPE html>
<html lang="en">

<head>
  <title>WishU</title>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="style.css">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css" />
</head>

<body>
  <div class="container">
    <div id="one" class="one">
      <h1>Hey
        <span id="name" class="name animate__delay-1s">Ayu Maulida Utami</span>
      </h1>
      <p class="two animate__delay-2s" id="greetingText">It's your birthday!!! :D</p>
    </div>
    <div class="three animate__delay-5s">
      I wanted to do something special, so I made this for you :)
    </div>
    <div class="wish" id="balloon-container">
      <img src="assets/01152 Happy Birthday.svg" class="wish-hbd animate__delay-5s center" alt="happy birthday">
      <br><br>
      <h5 class="wishText animate__delay-5s"><span id="wishText">There is no need for a special day to remind me how special you are and how
        important you are. The stars shine wherever you go.</span><br><span id="gradient-text">Happy 17<span
            id="seconds"></span><sup>nd</sup> Birthday</span> ;)</h5>
    </div>
    <div class="buttons">
      <a type="button" href="https://www.youtube.com/watch?v=k3zimSRKqNw" title="Follow you">
        <span class="heart animate__delay-5s"><span>Made with </span><img
            class="heart-icon animate__delay-5s" src="assets/icons8-diamond-heart-48.png"
            style="width: 18px;height: 15px;" alt="3" title="Hey D, :)"> by <span id="heartText">Architrixs</span></span>
      </a>
      <a type="button" class="refresh-btn animate__delay-5s" onClick="refreshPage()"><img
          src="assets/icons8-refresh-30.png" style="width: 23px;height: 23px;" alt="Refresh" title="Refresh"></a>
    </div>
  </div>
</body>
<script type="application/javascript" src="main.js"></script>

</html>

const animateCSS = (element, animation, delay, prefix = 'animate__') =>
  // create a Promise and return it
  new Promise((resolve, reject) => {
    const animationName = `${prefix}${animation}`;
    const node = document.querySelector(`.${element}`);

    node.classList.add(`${prefix}animated`, animationName);

    // When the animation ends, clean the classes and resolve the Promise
    function handleAnimationEnd(event) {
      event.stopPropagation();
      node.classList.remove(`${prefix}animated`, animationName);
      if (delay != 0) {
        setTimeout(() => { node.classList.add('invisible'); }, delay * 1000);
      }

      resolve('Animation ended');
    }

    node.addEventListener('animationend', handleAnimationEnd, { once: true });
  });

animateCSS('name', 'zoomIn', 4);
animateCSS('two', 'zoomIn', 2);
animateCSS('three', 'rotateIn', 6);
setTimeout(() => { document.querySelector('.one').classList.add('animate__animated', 'animate__zoomOut'); }, 6 * 800);
animateCSS('wish-hbd', 'fadeInUpBig', 0);
animateCSS('wishText', 'fadeIn', 0);
animateCSS('heart', 'bounceInLeft', 0);
animateCSS('refresh-btn', 'bounceIn', 0);
animateCSS('heart-icon', 'heartBeat', 0);


/* Balloon animation from https://codepen.io/Jemimaabu/pen/vYEYdOy */
function random(num) {
  return Math.floor(Math.random() * num)
}

function getRandomStyles() {
  var r = random(255);
  var g = random(255);
  var b = random(255);
  var mt = random(200);
  var ml = random(50);
  var dur = random(5) + 5;
  return `
  background-color: rgba(${r},${g},${b},0.7);
  color: rgba(${r},${g},${b},0.7); 
  box-shadow: inset -7px -3px 10px rgba(${r - 10},${g - 10},${b - 10},0.7);
  margin: ${mt}px 0 0 ${ml}px;
  animation: float ${dur}s ease-in infinite
  `
}

function createBalloons(num) {
  var balloonContainer = document.getElementById("balloon-container")
  for (var i = num; i > 0; i--) {
    var balloon = document.createElement("div");
    balloon.className = "balloon";
    balloon.style.cssText = getRandomStyles();
    balloonContainer.append(balloon);
  }
}

window.onload = function () {
  createBalloons(50);
}

// You can add a refresh Button using this...
// Play around with the HTML and CSS to use this correctly
function refreshPage() {
  window.location.reload();
}

// You can add a count up timer, ending at a a certain number, to Indicate Years...
// Play around with the HTML and CSS to use this correctly
var sec = 0;
function pad(val) { return val > 9 ? val : "0" + val; }
var timer = setInterval(function () {
  document.getElementById("seconds").innerHTML = pad(++sec % 60);
}, 1000);

setTimeout(function () {
  clearInterval(timer);
}, 22000);


// takes custom input from input.json from whichever field is not empty, otherwise html text is used.
const fetchData = () => {
  fetch("input.json")
    .then(data => data.json())
    .then(data => {
      Object.keys(data).map(key => {
        if (data[key] !== "") {
            //console.log(key,data[key])
            document.getElementById(key).innerText = data[key];
          }
        });
    });
}

fetchData();

@import url('https://fonts.googleapis.com/css2?family=Ubuntu&display=swap');
html {
    box-sizing: border-box;
}

body {
    margin: 0;
    background-color: mediumpurple;
    font-family: 'Ubuntu', sans-serif;
}

img {
    width: 500px;
    height: 400px;
}

a {
    text-decoration: none;
}

img.center {
    display: block;
    margin: 0 auto;
}

.animate__animated.animate__rotateIn {
    --animate-duration: 2s;
}
.animate__animated.animate__fadeInUpBig {
    --animate-delay: 2.5s;
}
.animate__animated.animate__fadeIn {
    --animate-delay: 2.8s;
}
.animate__animated.animate__bounceInLeft {
    --animate-delay: 3.5s;
}
.animate__animated.animate__heartBeat {
    --animate-delay: 3.7s;
    --animate-duration: 4s;
}
.animate__animated.animate__bounceIn {
    --animate-delay: 4.2s;
}
 
.invisible {
    opacity: 0;
}
.visible {
    opacity: 1;
}

.container {
    height: 100vh;
    width: 100vh;
    margin: 0 auto;
    text-align: center;
    position: relative;
    /* overflow: hidden; */
}
.container div.wish {
    top: 10vh;
    z-index: 1;
}
.container > div {
    position: absolute;
    left: 0;
    right: 0;
    top: 20vh;
}
  
.one {
    font-size: 2.5rem;
}
.two {
    font-size: 1.5rem;
    font-weight: lighter;
}
  
.three {
    font-size: 2.5rem;
    padding: 3px 5px;
    border-radius: 3px;
    display: inline-block;
}

#balloon-container {
    height: 100vh;
    top: 0vh;
    padding: 1em;
    box-sizing: border-box;
    display: flex;
    flex-wrap: wrap;
    overflow: hidden;
  }
  
  .balloon {
    height: 125px;
    width: 105px;
    border-radius: 75% 75% 70% 70%;
    position: relative;
  }
  
  .balloon:before {
    content: "";
    height: 75px;
    width: 1px;
    padding: 1px;
    background-color: #FDFD96;
    display: block;
    position: absolute;
    top: 125px;
    left: 0;
    right: 0;
    margin: auto;
  }
  
  .balloon:after {
      content: "▲";
      text-align: center;
      display: block;
      position: absolute;
      color: inherit;
      top: 120px;
      left: 0;
      right: 0;
      margin: auto;
  }
  
  @keyframes float {
    from {transform: translateY(100vh);
    opacity: 1;}
    to {transform: translateY(-300vh);
    opacity: 0;}
  }
/*
@keyframes rotate {
    from {
        transform: rotate(45deg);
    }
    to {
        transform: rotate(90deg);
    }
} */
.wish-hbd {
    height: 350px;
    position: relative;
    margin: 0;
    text-transform: uppercase;
  }
  
h5 {
    font-weight: lighter;
    font-size: 1.5rem;
    margin: 10px 0 0;
}

/* Remove `display: none` to use Refresh button and Count-up timer */
#seconds {
    display: none;
}

.refresh-btn {
    display: none;
    position: absolute;
    z-index: 5;
    height: 30px;
    width: 30px;
    cursor: pointer;
}

.container div.buttons {
    top: 94vh;
    z-index: 5;
}

#gradient-text {
    background-color: #ee1b1b;
    background-image: linear-gradient(45deg, #ff0000, #0d10aa);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
}

@media screen and (max-width: 500px) {
    .container {
      width: 90%;
    }
    .one {
        font-size: 2rem;
    }
    .three {
        font-size: 2.1rem;
    }
    .four {
      width: 90%;
    }
    .wish-hbd {
        font-size: 1.8rem;
      }
    
    h5 {
        font-size: 1.3rem;
      }
    img {
        width: 300px;
        height: 200px;
    }
    .refresh-btn {
        display: none;
    }
}
{
    "name": "Ayu Maulida Utami",
    "greetingText": "It's your birthday!!! :D",
    "wishText": "There is no need for a special day to remind me how special you are and how important you are. The stars shine wherever you go.",
    "heartText": "Happy birthday"
}
