<template>
  <section class="hero" @mousemove="onMouseMove">
    <div class="stars-layer"></div>
    <div class="stars-layer layer2"></div>

    <div class="container hero-container">
      <div class="hero-text">
        <p class="hello">Hello,</p>
        <h1 class="name">Babajanova Mahfuza</h1>
        <p class="job">Frontend Developer</p>
        <button @click="scrollToContact" class="btn-hero">Let’s Talk</button>
      </div>

      <div class="hero-image">
        <img src="/src/assets/me.png" alt="Mahfuza Photo" />
      </div>
    </div>

    
    <div class="cursor-light" ref="cursorLight"></div>
  </section>
</template>

<script setup>
import { ref } from "vue";

const cursorLight = ref(null);

const onMouseMove = (e) => {
  if (cursorLight.value) {
    cursorLight.value.style.left = `${e.clientX}px`;
    cursorLight.value.style.top = `${e.clientY}px`;
  }
};

const scrollToContact = () => {
  const contact = document.querySelector(".contact-me");
  if (contact) contact.scrollIntoView({ behavior: "smooth" });
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Playwrite+NO:wght@100..400&display=swap');

/* ----- HERO SECTION ----- */
.hero {
  position: relative;
  overflow: hidden;
  padding: 120px 20px;
  background: radial-gradient(circle at center, #0a0018, #050014, #02000c);
  color: #fff;
}

/* ----- STAR LAYERS (PARALLAX) ----- */
.stars-layer {
  position: absolute;
  inset: 0;
  background: url("https://i.ibb.co/YTbq4pp/stars.png");
  opacity: 0.5;
  animation: floatStars 40s linear infinite;
  z-index: 1;
}

.stars-layer.layer2 {
  background-size: 250%;
  opacity: 0.3;
  animation: floatStars2 65s linear infinite;
}

@keyframes floatStars {
  from { transform: translateY(0); }
  to { transform: translateY(-3000px); }
}

@keyframes floatStars2 {
  from { transform: translateY(0); }
  to { transform: translateY(-2000px); }
}

/* ----- CURSOR LIGHT ----- */
.cursor-light {
  position: fixed;
  width: 350px;
  height: 350px;
  background: radial-gradient(circle, rgba(140,0,255,0.4), transparent 70%);
  filter: blur(60px);
  pointer-events: none;
  transform: translate(-50%, -50%);
  z-index: 2;
  transition: 0.15s;
}

/* ----- CONTENT ----- */
.hero-container {
  display: flex;
  gap: 40px;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  z-index: 3;
  position: relative;
  animation: fadeUp 1.2s ease-out;
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

.hero-text {
  max-width: 460px;
  text-shadow: 0 0 8px rgba(160, 0, 255, 0.6);
}

/* Text Glow */
.hello {
  font-size: 1.6em;
  color: #d8b6ff;
  animation: glowPulse 3s ease-in-out infinite;
}

.name {
  font-size: 3em;
  margin: 10px 0;
  font-weight: 700;
  color: #ffffff;
  text-shadow: 0 0 12px rgba(200, 120, 255, 1),
               0 0 25px rgba(150, 0, 255, 0.9);

  font-family: "Playwrite NO", cursive;
  /* font-optical-sizing: auto;             */
}

.job {
  font-size: 1.4em;
  margin-bottom: 25px;
  color: #c9a4ff;
}

@keyframes glowPulse {
  0%, 100% { opacity: 0.9; text-shadow: 0 0 5px #b46aff; }
  50% { opacity: 1; text-shadow: 0 0 15px #d698ff; }
}

/* Button */
.btn-hero {
  padding: 14px 34px;
  background: linear-gradient(135deg, #b15bff, #7f00ff);
  border-radius: 12px;
  color: #fff;
  font-size: 1.2em;
  border: none;
  cursor: pointer;
  box-shadow: 0 0 12px rgba(170,0,255,0.7);
  transition: 0.3s ease;
}

.btn-hero:hover {
  box-shadow: 0 0 20px rgba(220, 140, 255, 1);
  transform: scale(1.05);
}

/* Image */
.hero-image img {
  width: 340px;
  border-radius: 20px;
  box-shadow: 0 0 35px rgba(160, 0, 255, 0.6);
  transition: transform 1s ease, box-shadow 1s ease;
}

.hero-image img:hover {
  transform: translateY(-10px);
  box-shadow: 0 0 50px rgba(200, 0, 255, 0.9);
}

/* Mobile */
@media (max-width: 768px) {
  .hero-container {
    flex-direction: column-reverse;
    text-align: center;
  }

  .hero-image img {
    width: 80%;
  }
}

</style>
