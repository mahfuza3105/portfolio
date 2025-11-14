<script setup>
import { ref } from "vue";

import AppHeader from './components/Header/AppHeaderHero.vue';
import AppNavbar from './components/Header/AppNavbar.vue';

import AppServices from './components/Services/AppServices.vue';
import AppProjects from './components/Projects/AppProjects.vue';
import AppContact from './components/Contact/AppContact.vue';

const activeSection = ref(null);

const toggleSection = (name) => {
  activeSection.value = activeSection.value === name ? null : name;
};
</script>

<template>
  <div class="page-wrapper">

    <AppNavbar />
    <AppHeader />

   
    <div class="mobile-buttons">
      <button @click="toggleSection('services')" class="mobile-btn">Services</button>
      <button @click="toggleSection('projects')" class="mobile-btn">Projects</button>
      <button @click="toggleSection('contact')" class="mobile-btn">Contact</button>
    </div>

    
    <section v-if="activeSection === 'services'" class="page-section mobile-section">
      <AppServices />
    </section>

    <section v-if="activeSection === 'projects'" class="page-section mobile-section">
      <AppProjects />
    </section>

    <section v-if="activeSection === 'contact'" class="page-section mobile-section">
      <AppContact />
    </section>

    
    <div class="desktop-sections">
      <section class="page-section">
        <AppServices />
      </section>

      <section class="page-section">
        <AppProjects />
      </section>

      <section class="page-section">
        <AppContact />
      </section>
    </div>

  </div>
</template>

<style scoped>

.mobile-buttons,
.mobile-section {
  display: none;
}

.desktop-sections {
  display: block;
}

@media (max-width: 900px) {
  
  .mobile-buttons {
    display: flex;
    flex-direction: column;
    gap: 15px;
    padding: 20px;
  }

  .mobile-btn {
    padding: 15px;
    font-size: 1.2em;
    border-radius: 12px;
    border: none;
    background: #7b1fa2;
    color: white;
    cursor: pointer;
  }

  .mobile-btn:hover {
    background: #5e0d86;
  }

  /* Показ секции */
  .mobile-section {
    display: block;
    padding: 20px;
  }

  /* Убираем обычные секции */
  .desktop-sections {
    display: none;
  }
}
</style>
