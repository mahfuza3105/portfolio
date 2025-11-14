<template>
  <section class="hero">
    <div class="container hero-container">
      <div class="hero-text">
        <p class="hello">Hello,</p>
        <h1 class="name">Babajanova Mahfuza</h1>
        <p class="job">Frontend Developer</p>
        <button @click="scrollToContact" class="btn-hero">Let’s Talk</button>
      </div>
      <div class="hero-image">
        <img src="/src/assets/me.png" alt="Mahfuza Photo">
      </div>
    </div>
  </section>
</template>

<script setup>
const scrollToContact = () => {
  const contact = document.querySelector('.contact-me');
  if (contact) {
    contact.scrollIntoView({ behavior: 'smooth' });
  }
};
</script>




<style scoped>
.hero {
  padding: 80px 20px;
  background: linear-gradient(135deg, #f3e5f5, #ffffff);
}

.hero-container {
  display: flex;
  align-items: center;
  justify-content: center; 
  flex-wrap: wrap;
  gap: 20px; 
}

.hero-text {
  max-width: 450px; 
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  margin: 0; 
}

.hero-text .hello {
  font-size: 1.5em;
  color: #5e0d86;
}

.hero-text .name {
  font-size: 2.8em;
  font-weight: bold;
  margin: 10px 0;
  color: #4a0072;
}

.hero-text .job {
  font-size: 1.3em;
  margin-bottom: 25px;
  color: #6a1b9a;
}

.btn-hero {
  padding: 12px 30px;
  border: none;
  border-radius: 10px;
  background-color: #7b1fa2;
  color: white;
  font-size: 1.1em;
  cursor: pointer;
  transition: background 0.3s;
}

.btn-hero:hover {
  background-color: #5e0d86;
}

.hero-image {
  max-width: 600px;
  display: flex;
  justify-content: center;
}

.hero-image img {
  width: 100%;
  height: auto;
  border-radius: 15px;
}

.container {
  margin-left: auto;
  margin-right: auto;
}

@media (max-width: 900px) {
  .hero-container {
    flex-direction: column-reverse;
    text-align: center;
    gap: 15px;
  }
  .hero-image img {
    width: 100%;
    height: auto;
  }
}

</style>
