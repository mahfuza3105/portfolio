<template>
  <section class="about-me">
    <div class="container">
      <h2>About Me</h2>
      <h3>What I actually love to do</h3>
      <div class="love-grid">
        <div class="love-item" v-for="(item, index) in loveItems" :key="index">
          <p>{{ item }}</p>
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
        "Hi! I’m Mahfuza, a passionate front-end developer who loves turning ideas into interactive web experiences. I enjoy coding, learning new technologies, and creating projects that not only look good but also work smoothly.",
        "When I’m not coding, you can find me exploring anime, experimenting with design, or challenging myself with new projects. My goal is to grow as a developer and make the web a more creative place.",
        "I also love sharing knowledge, collaborating with others, and constantly improving my skills. Building something that helps people or brings joy is what motivates me every day."
      ]
    }
  }
};
</script>

<style scoped>
.about-me {
  padding: 80px 20px;
  background: linear-gradient(to right, #f3e5f5, #e1bee7);
  font-family: 'Poppins', sans-serif;
  color: #333;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}

h2 {
  font-size: 3em;
  margin-bottom: 20px;
  text-align: center;
  background: linear-gradient(90deg, #7b1fa2, #9c27b0, #d500f9);
  
  -webkit-text-fill-color: transparent;
  font-weight: 700;
}

h3 {
  font-size: 2em;
  margin-bottom: 50px;
  text-align: center;
  color: #6a1b9a;
  font-weight: 500;
}

.love-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
}

.love-item {
  background: #fff;
  padding: 30px;
  border-radius: 25px;
  box-shadow: 0 10px 25px rgba(156,39,176,0.1);
  transition: transform 0.4s ease, box-shadow 0.4s ease;
  line-height: 1.7;
  text-align: justify;
  font-size: 1.05em;
  color: #4a0072;
}

.love-item:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(156,39,176,0.25);
}

@media (max-width: 900px) {
  h2 {
    font-size: 2.2em;
  }
  h3 {
    font-size: 1.6em;
  }
  .love-item {
    font-size: 1em;
  }
}
</style>
