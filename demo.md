---
title: Demo
layout: layouts/page.njk
tags: 
date: 2024-02-26
---

## Hello

Yo this is a test, testing if p5.js, buttons, image modals and more work well with my site.

<a class="flat-button" href="Resume.pdf" target="_blank">Download My Resume 📄</a>
        <a class="flat-button" href="https://www.buymeacoffee.com/jleyba92K" target="_blank">Buy Me A Tea 🍵</a>

<style>
    #blog-threejs canvas {
      /* force the canvas to fill out the entire area */
      width: 100%!important; height: 100%!important; 

      /* force the z-pos of the canvas to be on-top */
      z-index: -1; 
    }
    canvas {
		position: fixed;
		left: 0;
		top: 0;
		z-index: -1;
	}
</style>
<script>
let particles = [];
class Particle {
// setting the co-ordinates, radius and the
// speed of a particle in both the co-ordinates axes.
  constructor(){
    this.x = random(0,width);
    this.y = random(0,height);
    this.r = random(1,8);
    this.xSpeed = random(-2,2);
    this.ySpeed = random(-1,1.5);
  }

// creation of a particle.
  createParticle() {
    noStroke();
    //fill('rgba(200,169,169,0.5)');
    fill('#254e70');
    circle(this.x,this.y,this.r);
  }

// setting the particle in motion.
  moveParticle() {
    if(this.x < 0 || this.x > width)
      this.xSpeed*=-1;
    if(this.y < 0 || this.y > height)
      this.ySpeed*=-1;
    this.x+=this.xSpeed;
    this.y+=this.ySpeed;
  }

// this function creates the connections(lines)
// between particles which are less than a certain distance apart
  joinParticles(particles) {
    particles.forEach(element =>{
      let dis = dist(this.x,this.y,element.x,element.y);
      if(dis<85) {
        //stroke('rgba(255,255,255,0.04)');
        stroke('#c2cae8');
        line(this.x,this.y,element.x,element.y);
      }
    });
  }

  drawLines(particles) {
    particles.forEach(element =>{
      let dis = dist(this.x,this.y,element.x,element.y);
      if(dis<85) {
        stroke('#c2cae8');
        line(this.x,this.y,element.x,element.y);
      }
    });
  }
}

function setup() {
  let canvas = createCanvas(windowWidth, windowHeight);
  canvas.id('pageCanvas');
  
  for(let i = 0;i<width/10;i++){
    particles.push(new Particle());
  }
}

function draw() {
    background('#f7f7ff');
  for(let i = 0;i<particles.length;i++) {
    particles[i].createParticle();
    particles[i].moveParticle();
    particles[i].joinParticles(particles.slice(i));
  }
}




function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
</script>
<img class="border-image" src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/cc/Air_Force_Ensign_of_the_United_Kingdom.svg/1920px-Air_Force_Ensign_of_the_United_Kingdom.svg.png"/>
<div id="blog-threejs"></div>
