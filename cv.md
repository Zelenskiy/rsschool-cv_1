## rsschool-cv

**********************************
## Oleksandr Zelenskyi

**********************************
### Junior Frontend Developer

**********************************
### Contact information:
* Phone: +380973582250
* E-Mail: alexandr.s.zelenskiy@gmail.com
* Telegram: https://t.me/alex_zelenskiy
* Skype: Zelensk1973
* Discord: Oleksandr (Zelenskiy)

**********************************
### Briefly About Myself:
I possess a foundation in computer science and physics, enabling me to apply my analytical and logical abilities in software development and testing. With over two decades of experience collaborating with others, I am adept at working in teams and have a strong interest in staying updated on industry news and emerging technologies. I have a knack for rapid learning and effective time management.

**********************************
### Skills and Proficiency:
* HTML5, CSS3
* JavaScript Basics
* React
* Git, GitHub
* VS Code, IntelliJ IDEA
* Python, Django, Flask
* SQL
* Adobe Photoshop

**********************************
### Soft Skills
I am outgoing and excel at teamwork. I possess a rapid learning capability, a strong aptitude for researching and retrieving information, and the ability to analyze and succinctly summarize data.
**********************************

### Code examples:

```
const canvas = document.getElementById("myCanvas");
const started = document.getElementById("started");
const reset = document.getElementById("reset");
const kol = document.getElementById("kol");
const seconds = document.getElementById("seconds");
const speed = document.getElementById("speed");
const accel = document.getElementById("accel");
const mass_1 = document.getElementById("mass_1");
const mass_2 = document.getElementById("mass_2");

const ctx = canvas.getContext("2d");


class MovingBody {
 
  constructor(
    mass, mass2,
    μ,
    x,
    y,
    Vx,
    Vy,    
    Fx,
    Fy
  ) {
    this.m1 = mass;
    this.m2 = mass2;
    this.μ = μ,
    this.Vx = Vx;
    this.Vy = Vy;
    this.x = x;
    this.y = y;
    this.ax = g * (this.m2 - this.μ * this.m1)/(this.m1+this.m2);
  }

  reset = () =>{
    this.Vx = 0;
    this.Vy = 0;
    this.x = x0;
    this.y = y0;
    this.draw()
    seconds.innerText = "00.00";
    speed.innerText = "0.00";
    accel.innerText = "0.00";
    started.innerText = "Пуск"
    this.m1 = parseFloat(mass_1.value);
    this.m2 = parseFloat(mass_2.value);
    this.ax = g * (this.m2 - this.μ * this.m1)/(this.m1+this.m2);
    
  }

  draw = () =>{
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = "brown";
    ctx.fillRect(this.x, this.y, width, height);
    drawLine(this.x + width , this.y + height/2, 508, this.y + height/2)
    const l1 = 508 - this.x + width;
    const l2 = 508 - l1 + 20;
    drawLine(520 , this.y + height/2 + 8, 520, this.y + height/2 + l2 - 10)
    ctx.fillStyle = "red";
    const widthGruz = 30
    const heightGruz = 10
    ctx.fillRect(520-widthGruz/2, this.y + l2, widthGruz, heightGruz);
    // Малюємо вектори


  }
  
  update = () =>{
    if (isStarted) {
      if (this.ax<=0) {
        this.ax = 0;
        kol.classList.remove("rotate-img")
      
      }
        
        if (this.x > widthTribometr-10 ) {
            started.checked = false;
            kol.classList.remove("rotate-img");
        } else {
          this.Vx += this.ax * t
          this.x += this.Vx * t;
        }
    
        this.draw();
        let x = (parseFloat(seconds.innerText) + t*coefT).toFixed(2)
        if (x<10) {x ='0'+x};
        seconds.innerText= x
        x = (parseFloat(this.Vx) + t).toFixed(2)
        speed.innerText= x
        x = (parseFloat(this.ax) ).toFixed(2)
        accel.innerText= x


      }
  }
}

function drawLine(x1, y1, x2, y2) {
    ctx.strokeStyle = "blue";  
    ctx.beginPath();  
    ctx.moveTo(x1, y1);  
    ctx.lineTo(x2, y2);  
    ctx.stroke();
  }

  const metr = document.getElementById('draggable');

  metr.onmousedown = function(e) {

    var coords = getCoords(metr);
    var shiftX = e.pageX - coords.left;
    var shiftY = e.pageY - coords.top;
  
    metr.style.position = 'absolute';
    document.body.appendChild(metr);
    moveAt(e);
  
    metr.style.zIndex = 1000; 
  
    function moveAt(e) {
      metr.style.left = e.pageX - shiftX + 'px';
      metr.style.top = e.pageY - shiftY + 'px';
    }
  
    document.onmousemove = function(e) {
      moveAt(e);
    };
  
    metr.onmouseup = function() {
      document.onmousemove = null;
      metr.onmouseup = null;
    };
  
  }
  
  metr.ondragstart = function() {
    return false;
  };
  
  function getCoords(elem) { 
    var box = elem.getBoundingClientRect();
    return {
      top: box.top + pageYOffset,
      left: box.left + pageXOffset
    };
  }

  var draggable = document.getElementById('draggable');
  var offsetX, offsetY;
  var isDragging = false;

  draggable.addEventListener('touchstart', function(e) {
    var touch = e.touches[0];
    offsetX = touch.clientX - draggable.getBoundingClientRect().left;
    offsetY = touch.clientY - draggable.getBoundingClientRect().top;
    isDragging = true;
  });

  draggable.addEventListener('touchmove', function(e) {
    if (!isDragging) return;
    var touch = e.touches[0];
    var left = touch.clientX - offsetX;
    var top = touch.clientY - offsetY;

    draggable.style.left = left + 'px';
    draggable.style.top = top + 'px';

    e.preventDefault(); // Забороняємо прокрутку сторінки під час перетягування
  });

  draggable.addEventListener('touchend', function() {
    isDragging = false;
  });




const g = 9.81;

let m1 = 0.35;
let m2 = 0.1;
let μ = 0.25;
const x0 = 70;
const y0 = 50;
const t = 0.30
const coefT = 0.05
const coefL = 0.05
let isStarted = false;


const movingRectangle = new MovingBody(m1, m2, μ, x0, y0, 2,  0, 1, 0);
const width = 50;
const height = 30;
const widthTribometr = 378+70;
movingRectangle.reset();


reset.addEventListener("click", () => {
  isStarted = false;
  movingRectangle.reset();
    
});

started.addEventListener("click", () => {  
  isStarted = !isStarted;
  if (isStarted) {
    kol.classList.add("rotate-img");
    started.innerText = "Пауза"
  } else {
    kol.classList.remove("rotate-img");
    started.innerText = "Пуск"
  }
});


function animate() {
  movingRectangle.update();
  requestAnimationFrame(animate);
}

animate();

```

**********************************
### Experience:
* Site development: https://znz16300.github.io/site/

**********************************
### Education:

*I earned my degree from Chernihiv State Pedagogical Institute in 1996. 
*Additionally, I successfully completed the "Fundamentals of Software Testing" course at QATestLab in 2023 and the "JavaScript/Front-end" course at RSSchool.
**********************************
### Languages:
* English - Pre-intermediate
* Ukrainian - Native
* Russian - Intermediate
