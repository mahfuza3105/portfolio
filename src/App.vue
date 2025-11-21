<script setup>
import AppHeader from './components/Header/AppHeaderHero.vue';
import AppNavbar from './components/Header/AppNavbar.vue';
import AboutMe from './components/Services/AboutMe.vue';
import AppProjects from './components/Projects/AppProjects.vue';
import AppContact from './components/Contact/AppContact.vue';
</script>

<template>
  <div class="page-wrapper">
    <AppNavbar />
    <AppHeader />

    
    <div class="responsiv">
      <AboutMe/>
      
    <AppProjects />
    <AppContact />
    </div>
  </div>
</template>
<style scoped>

.page-wrapper {
  display: flex;
  flex-direction: column;
  gap: 50px; 
  padding: 20px;
}
@media (max-width: 900px) {
  .page-wrapper {
    gap: 30px; 
    padding: 10px;
  }
  .responsiv{
    display: none;
  }
}
</style>
