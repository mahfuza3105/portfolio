<script setup>
import { ref, onMounted } from 'vue';
import AppHeader from './components/Header/AppHeaderHero.vue';
import AppNavbar from './components/Header/AppNavbar.vue';
import AboutMe from './components/Services/AboutMe.vue';
import AppProjects from './components/Projects/AppProjects.vue';
import AppContact from './components/Contact/AppContact.vue';

const activeSection = ref('about');
const isMobile = ref(false);

const showSection = (section) => {
  activeSection.value = section;
};

const checkMobile = () => {
  isMobile.value = window.innerWidth <= 900;
};

onMounted(() => {
  checkMobile();
  window.addEventListener('resize', checkMobile);
});
</script>

<template>
  <div class="page-wrapper">
    <AppNavbar @change-section="showSection" />
    <AppHeader />

    <div class="sections">
      
      <template v-if="!isMobile">
        <AboutMe />
        <AppProjects />
        <AppContact />
      </template>

       
      <template v-else>
        <AboutMe v-if="activeSection === 'about'" />
        <AppProjects v-if="activeSection === 'works'" />
        <AppContact v-if="activeSection === 'contact'" />
      </template>
    </div>
  </div>
</template>

<style scoped>
.page-wrapper {
  display: flex;
  flex-direction: column;
  /* gap: 50px;  */
  
}
@media (max-width: 900px) {
  .page-wrapper {
    gap: 30px;
    padding: 10px;
  }
}
</style>
