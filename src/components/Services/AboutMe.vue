<template>
  <section class="about-me">
    <div class="container">
      <h3>About Me</h3>
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
        "Hi! I’m Mahfuza, a passionate Frontend Developer who loves turning ideas into interactive web experiences. I enjoy coding with Vue.js, React, JavaScript, HTML, and CSS. I also know English, which I use for reading documentation and collaborating on projects.",
        "I love playing chess and have achieved 1st and 2nd places in regional competitions. Chess helps me develop logic, strategy, and patience, skills I also apply in web development.",
        "I enjoy learning new technologies, improving my skills, and sharing knowledge. My goal is to create web projects that are not only functional but also visually appealing and user-friendly."
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
  h3 {
    font-size: 1.6em;
  }
  .love-item {
    font-size: 1em;
  }
}
</style>
