<template>
  <section class="contact-me">
    <div class="stars"></div>
    <div class="stars2"></div>
    <div class="stars3"></div>

    <div class="container">
      <h2 class="title">Contact Me</h2>
      <p class="subtitle">Feel free to reach out via phone or social media 💜</p>

      <div class="contact-cards">
        <div
          class="contact-card"
          v-for="card in contact"
          :key="card.title"
          @mousemove="onCardMove"
          @mouseleave="onCardLeave"
        >
          <h3>{{ card.icon }} {{ card.title }}</h3>
          <p>
            <a :href="card.link" target="_blank">{{ card.value }}</a>
          </p>
          <span class="neon-ring"></span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "ContactMe",
  data() {
    return {
      contact: [
        { title: "Phone", icon: "📞", value: "+998 33 960 08 81", link: "tel:+998339600881" },
        { title: "Instagram", icon: "📸", value: "@mahfuza_0509", link: "https://instagram.com/mahfuza_0509" },
        { title: "Telegram", icon: "💬", value: "@mahfuza_3105", link: "https://t.me/mahfuza_3105" },
        { title: "GitHub", icon: "🐱", value: "github.com/mahfuza3105", link: "https://github.com/mahfuza3105" }
      ]
    };
  },

  methods: {
    onCardMove(e) {
      const card = e.currentTarget;
      const rect = card.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;

      const rotateX = (y / rect.height - 0.5) * 10;
      const rotateY = (x / rect.width - 0.5) * -10;

      card.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale(1.05)`;
    },
    onCardLeave(e) {
      const card = e.currentTarget;
      card.style.transform = `rotateX(0) rotateY(0) scale(1)`;
    }
  }
};
</script>

<style scoped>

.contact-me {
  padding: 100px 20px;
  background: radial-gradient(circle at top, #150028, #0a0014, #000);
  color: #e9d4ff;
  text-align: center;
  font-family: "Poppins", sans-serif;
  position: relative;
  overflow: hidden;
}


.stars,
.stars2,
.stars3 {
  position: absolute;
  width: 2000px;
  height: 2000px;
  top: -1000px;
  left: -1000px;
  background-repeat: repeat;
  animation: starMove 60s linear infinite;
}

.stars {
  background-image: radial-gradient(2px 2px at 20px 20px, #ffffffaa, transparent),
                    radial-gradient(2px 2px at 400px 350px, #ffffffcc, transparent),
                    radial-gradient(1px 1px at 800px 600px, #ffffff55, transparent);
  opacity: 0.6;
}

.stars2 {
  background-image: radial-gradient(2px 2px at 100px 80px, #b36bff, transparent),
                    radial-gradient(2px 2px at 600px 300px, #d18fff, transparent);
  opacity: 0.4;
  animation-duration: 85s;
}

.stars3 {
  background-image: radial-gradient(1px 1px at 200px 200px, #ffd6ff, transparent),
                    radial-gradient(2px 2px at 900px 500px, #ffb3ff, transparent);
  opacity: 0.2;
  animation-duration: 120s;
}

@keyframes starMove {
  from { transform: translateY(0); }
  to { transform: translateY(600px); }
}

/* ===== TITLE ===== */
.title {
  font-size: 3.2em;
  margin-bottom: 10px;
  color: #eac1ff;
  text-shadow: 0 0 18px rgba(200, 80, 255, 1);
  animation: fadeDown 1s ease;
}

.subtitle {
  margin-bottom: 50px;
  opacity: 0.8;
  font-size: 1.2em;
  animation: fadeUp 1s ease;
}

@keyframes fadeDown {
  from { opacity: 0; transform: translateY(-20px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* ===== GRID ===== */
.contact-cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 25px;
}

/* ===== CARDS ===== */
.contact-card {
  position: relative;
  width: 240px;
  padding: 25px;
  border-radius: 18px;

  background: rgba(60, 0, 100, 0.35);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(185, 0, 255, 0.25);

  box-shadow: 0 0 25px rgba(180, 0, 255, 0.3);
  transition: 0.25s ease;
  transform-style: preserve-3d;
  cursor: pointer;
}

.contact-card h3 {
  color: #f4d9ff;
  margin-bottom: 8px;
  font-size: 1.3em;
  text-shadow: 0 0 12px rgba(190, 0, 255, 0.7);
}

.contact-card a {
  color: #e1c3ff;
  text-decoration: none;
  text-shadow: 0 0 8px rgba(180, 0, 255, 0.5);
}

.contact-card:hover a {
  text-decoration: underline;
}

/* ===== NEON BORDER ===== */
.neon-ring {
  content: "";
  pointer-events: none;
  position: absolute;
  inset: 0;
  border-radius: 18px;
  border: 2px solid transparent;
  background: linear-gradient(135deg, rgba(180,0,255,0.8), rgba(255,120,255,0.7)) border-box;
  mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
  opacity: 0;
  transition: opacity 0.4s ease;
}

.contact-card:hover .neon-ring {
  opacity: 1;
}

/* ===== RESPONSIVE ===== */
@media (max-width: 700px) {
  .title { font-size: 2.3em; }
  .contact-card { width: 85%; }
}
</style>
