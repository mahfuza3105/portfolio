<template>
  <section class="about-me">
    <div class="container">
      <h3 class="title">About Me</h3>

      <div class="love-grid">
        <div 
          class="love-item"
          v-for="(item, index) in loveItems"
          :key="index"
          @mousemove="cardTilt"
          @mouseleave="resetTilt"
        >
          <p>{{ item }}</p>
          <span class="neon-border"></span>
        </div>
      </div>

    </div>
  </section>
</template>

<script>
export default {
  name: "AboutMe",
  data() {
    return {
      loveItems: [
        "Hi! I’m Mahfuza, a passionate Frontend Developer who loves turning ideas into interactive web experiences. I enjoy coding with Vue.js, React, JavaScript, HTML, and CSS. I also know English, which I use for reading documentation and collaborating on projects.",
        "I love playing chess and have achieved 1st and 2nd places in regional competitions. Chess helps me develop logic, strategy, and patience, skills I also apply in web development.",
        "I enjoy learning new technologies, improving my skills, and sharing knowledge. My goal is to create web projects that are not only functional but also visually appealing and user-friendly."
      ]
    };
  },
  methods: {
    cardTilt(e) {
      const card = e.currentTarget;
      const rect = card.getBoundingClientRect();

      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;

      const rotateX = (y / rect.height - 0.5) * 15;
      const rotateY = (x / rect.width - 0.5) * -15;

      card.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale(1.05)`;
    },
    resetTilt(e) {
      const card = e.currentTarget;
      card.style.transform = `rotateX(0deg) rotateY(0deg) scale(1)`;
    }
  }
};
</script>

<style scoped>
.about-me {
  padding: 100px 20px;
  background: radial-gradient(circle at top, #0d001e, #050012, #02000a);
  font-family: 'Poppins', sans-serif;
  color: #e7d9ff;
  position: relative;
  overflow: hidden;
}

/* Light glow background */
.about-me::before {
  content: "";
  position: absolute;
  width: 800px;
  height: 800px;
  background: radial-gradient(circle, rgba(160, 0, 255, 0.25), transparent 70%);
  top: -200px;
  left: -100px;
  filter: blur(120px);
  animation: glowMove 15s infinite alternate ease-in-out;
}

@keyframes glowMove {
  from { transform: translateX(0); }
  to { transform: translateX(120px); }
}

.title {
  font-size: 2.4em;
  margin-bottom: 60px;
  text-align: center;
  color: #d7b0ff;
  text-shadow: 0 0 15px rgba(190, 60, 255, 0.8);
  animation: fadeDown 1s ease-out;
}

@keyframes fadeDown {
  from { opacity: 0; transform: translateY(-20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* GRID */
.love-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 35px;
  z-index: 2;
}

/* CARD */
.love-item {
  position: relative;
  background: rgba(35, 0, 65, 0.35);
  padding: 30px;
  border-radius: 22px;
  box-shadow: 0 0 18px rgba(150, 0, 255, 0.2);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(200, 0, 255, 0.25);

  transition: 
    transform 0.25s ease-out,
    box-shadow 0.25s ease-out;

  line-height: 1.75;
  font-size: 1.05em;
  color: #e8ccff;
  transform-style: preserve-3d;

  animation: fadeCard 1.2s ease forwards;
  opacity: 0;
}

@keyframes fadeCard {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Neon edge glow */
.neon-border {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: 22px;
  pointer-events: none;
  border: 2px solid transparent;
  background: linear-gradient(135deg, rgba(150, 0, 255, 0.7), rgba(255, 170, 255, 0.5)) border-box;
  mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
  opacity: 0;
  transition: 0.5s;
}

.love-item:hover .neon-border {
  opacity: 1;
  box-shadow: 0 0 25px rgba(200, 0, 255, 0.8);
}

/* Hover Glow */
.love-item:hover {
  box-shadow: 0 0 40px rgba(200, 0, 255, 0.55);
}

/* RESPONSIVE */
@media (max-width: 900px) {
  .title { font-size: 2em; }
  .love-item { font-size: 1em; }
}
</style>
