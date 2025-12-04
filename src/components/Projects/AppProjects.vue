<template>
  <section class="creative-projects">
    <div class="container">
      <h2 class="title">All Creative Projects</h2>

      <div class="projects-grid">
        <div 
          class="project-card" 
          v-for="project in projects" 
          :key="project.id"
          @mousemove="onCardMove"
          @mouseleave="onCardLeave"
        >
          <div class="image-wrapper">
            <img :src="project.image" :alt="project.title" />
          </div>

          <h3>{{ project.title }}</h3>
          <p>{{ project.description }}</p>

          <button class="view-btn">View Project</button>

          <!-- неоновая рамка -->
          <span class="neon-ring"></span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import zooImg from '/src/assets/zoo.png';
import newsImg from '/src/assets/news.png';
import marketImg from '/src/assets/market.png';
import youtubeImg from '/src/assets/LogosYoutube.png';

export default {
  name: "CreativeProjects",
  data() {
    return {
      projects: [
        { id: 1, title: "Zoo Animal Registration", description: "A management system to register and track animals in a zoo.", image: zooImg },
        { id: 2, title: "News Website", description: "A responsive news website with multiple categories and modern design.", image: newsImg },
        { id: 3, title: "Editable Transfer Market", description: "React app to manage football transfers, add/remove players interactively.", image: marketImg },
        { id: 4, title: "YouTube-Like Video Platform", description: "A front-end project mimicking YouTube layout with videos and cards.", image: youtubeImg },
      ]
    };
  },

  methods: {
    onCardMove(e) {
      const card = e.currentTarget;
      const rect = card.getBoundingClientRect();

      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;

      const rotateX = (y / rect.height - 0.5) * 15;
      const rotateY = (x / rect.width - 0.5) * -15;

      card.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale(1.06)`;
    },

    onCardLeave(e) {
      const card = e.currentTarget;
      card.style.transform = `rotateX(0) rotateY(0) scale(1)`;
    }
  }
};
</script>

<style scoped>
/* ===== SECTION ===== */
.creative-projects {
  padding: 100px 20px;
  background: radial-gradient(circle at bottom, #0b001c, #040012, #02000a);
  font-family: "Poppins", sans-serif;
  position: relative;
  overflow: hidden;
}

/* Фоновое сияние */
.creative-projects::before {
  content: "";
  position: absolute;
  width: 1000px;
  height: 1000px;
  background: radial-gradient(circle, rgba(160, 0, 255, 0.35), transparent 70%);
  bottom: -350px;
  right: -250px;
  filter: blur(140px);
  animation: moveGlow 16s ease-in-out infinite alternate;
}

@keyframes moveGlow {
  from { transform: translateX(0px); opacity: 0.7; }
  to { transform: translateX(-120px); opacity: 1; }
}

/* ===== TITLE ===== */
.title {
  text-align: center;
  font-size: 3.2em;
  margin-bottom: 60px;
  color: #e9c9ff;
  text-shadow: 0 0 18px rgba(200, 80, 255, 1);
  animation: fadeInDown 1s ease-out;
}

@keyframes fadeInDown {
  from { opacity: 0; transform: translateY(-25px); }
  to { opacity: 1; transform: translateY(0); }
}

/* ===== GRID ===== */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 35px;
}

/* ===== CARD ===== */
.project-card {
  position: relative;
  background: rgba(55, 0, 95, 0.25);
  border-radius: 20px;
  overflow: hidden;
  padding: 20px 0 30px;
  text-align: center;

  backdrop-filter: blur(15px);
  border: 1px solid rgba(185, 0, 255, 0.25);

  transform-style: preserve-3d;

  box-shadow: 0 0 25px rgba(150, 0, 255, 0.25);
  transition: 0.25s ease-out;

  animation: fadeUp 1.2s ease both;
  opacity: 0;
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Неоновая рамка */
.neon-ring {
  content: "";
  pointer-events: none;
  position: absolute;
  inset: 0;
  border-radius: 20px;
  border: 2px solid transparent;
  background: linear-gradient(135deg, rgba(180,0,255,0.8), rgba(255,150,255,0.6)) border-box;
  mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
  opacity: 0;
  transition: opacity 0.5s ease;
}

.project-card:hover .neon-ring {
  opacity: 1;
}

/* ===== IMAGE ===== */
.image-wrapper {
  overflow: hidden;
  border-radius: 18px 18px 0 0;
}

.project-card img {
  width: 100%;
  height: 180px;
  object-fit: cover;
  transition: transform 0.6s ease;
}

.project-card:hover img {
  transform: scale(1.14) translateY(-8px);
}

/* ===== TEXT ===== */
.project-card h3 {
  margin: 20px 0 10px;
  font-size: 1.5em;
  font-weight: 600;
  color: #e9b8ff;
  text-shadow: 0 0 12px rgba(180, 0, 255, 0.9);
}

.project-card p {
  padding: 0 20px;
  font-size: 1em;
  line-height: 1.5;
  color: #e8d7ff;
}

/* ===== BUTTON ===== */
.view-btn {
  margin-top: 15px;
  padding: 10px 25px;
  font-size: 1em;
  color: #fff;

  background: linear-gradient(135deg, #b45bff, #7f00ff);
  border: none;
  border-radius: 40px;

  cursor: pointer;
  transition: 0.3s ease;
  box-shadow: 0 0 15px rgba(180,0,255,0.7);
}

.view-btn:hover {
  transform: scale(1.07);
  box-shadow: 0 0 25px rgba(220,140,255,1);
}

/* ===== RESPONSIVE ===== */
@media (max-width: 900px) {
  .title { font-size: 2.3em; }
}
</style>
