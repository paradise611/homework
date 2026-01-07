<template>
<canvas ref="canvas"></canvas>

</template>
<style scoped>
    canvas{
    
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 2;
}
    </style>
<script setup>
    import { ref, onMounted, onUnmounted } from 'vue';

const canvas = ref(null);
let ctx = null;
let particles = [];
const particleCount = 80;
let animationFrameId = null;


class SakuraParticle {
  constructor(canvasWidth, canvasHeight) {
    this.x = Math.random() * canvasWidth;
    this.y = Math.random() * canvasHeight - canvasHeight;
    this.size = Math.random() * 8 + 4;
    this.speedY = Math.random() * 1 + 0.5;
    this.speedX = Math.random() * 1 - 0.5;
    this.alpha = Math.random() * 0.5 + 0.3;
    this.angle = Math.random() * Math.PI * 2;
    this.spinSpeed = (Math.random() - 0.5) * 0.02;
  }

  update(canvasWidth, canvasHeight) {
    this.y += this.speedY;
    this.x += this.speedX;
    this.angle += this.spinSpeed;
    
    if (this.y > canvasHeight) {
      this.x = Math.random() * canvasWidth;
      this.y = Math.random() * canvasHeight - canvasHeight; 
      this.alpha = Math.random() * 0.5 + 0.3;
    }
  }

  draw() {
    if (!ctx) return;
    
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2); 
    ctx.fillStyle = `rgba(255, 182, 193, ${this.alpha})`;
    ctx.fill();
  }
}


const animate = () => {
  if (!ctx || !canvas.value) return;

  ctx.clearRect(0, 0, canvas.value.width, canvas.value.height); 
  
  
  
  particles.forEach(particle => {
    particle.update(canvas.value.width, canvas.value.height);
    particle.draw();
  });
  
  animationFrameId = requestAnimationFrame(animate);
};


const resize = () => {
  if (canvas.value) {
    canvas.value.width = window.innerWidth;
    canvas.value.height = window.innerHeight;
  }
};

const initParticles = () => {
  particles = [];
  if (canvas.value) {
    for (let i = 0; i < particleCount; i++) {
      particles.push(new SakuraParticle(canvas.value.width, canvas.value.height));
    }
  }
};


onMounted(() => {
  ctx = canvas.value.getContext('2d');
  resize();
  initParticles();
  window.addEventListener('resize', resize);
  animate();
});

onUnmounted(() => {
  cancelAnimationFrame(animationFrameId);
  window.removeEventListener('resize', resize);
});
</script>