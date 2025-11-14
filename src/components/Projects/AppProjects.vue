<template>
  <section class="creative-projects">
    <div class="container">
      <h2>All Creative Projects</h2>
      <div class="projects-grid">
        <div class="project-card" v-for="project in projects" :key="project.id">
          <div class="image-wrapper">
            <img :src="project.image" :alt="project.title" />
          </div>
          <h3>{{ project.title }}</h3>
          <p>{{ project.description }}</p>
          <button class="view-btn">View Project</button>
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
      ],
    };
  },
};
</script>

<style scoped>
.creative-projects {
  padding: 80px 20px;
  background: linear-gradient(135deg, #f3e5f5, #e1bee7); /* светлый фиолетовый градиент */
  font-family: 'Poppins', sans-serif;
  color: #333;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

h2 {
  font-size: 3em;
  text-align: center;
  margin-bottom: 50px;
  font-weight: 700;
  background: linear-gradient(90deg, #9c27b0, #673ab7); /* фиолетовый градиент текста */
  
  -webkit-text-fill-color: transparent;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 30px;
}

.project-card {
  background: #fff;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 15px 35px rgba(156,39,176,0.2);
  transition: transform 0.4s ease, box-shadow 0.4s ease;
  text-align: center;
  padding-bottom: 20px;
  position: relative;
}

.image-wrapper {
  overflow: hidden;
  border-radius: 20px 20px 0 0;
}

.project-card img {
  width: 100%;
  height: 180px;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.project-card:hover img {
  transform: scale(1.1);
}

.project-card h3 {
  margin: 20px 0 10px;
  font-size: 1.5em;
  font-weight: 600;
  color: #6a1b9a;
}

.project-card p {
  padding: 0 15px;
  font-size: 1em;
  line-height: 1.5;
  color: #555;
}

.view-btn {
  margin-top: 15px;
  padding: 10px 25px;
  font-size: 0.95em;
  color: #fff;
  background: linear-gradient(135deg, #9c27b0, #673ab7);
  border: none;
  border-radius: 50px;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.view-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 20px rgba(103,58,183,0.4);
}

.project-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(103,58,183,0.25);
}
</style>
