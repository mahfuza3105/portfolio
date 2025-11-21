<template>
  <header class="header">
    <div class="container header_navbar">
      <a href="#"><img src="/src/assets/image.png" alt="logo" class="logo" /></a>
      
      <ul :class="['header_menu', { 'show-menu': menuOpen }]">
        <li class="header_menu--item"><a href="#about" class="header_link">About</a></li>
        
        <li class="header_menu--item"><a href="#works" class="header_link">Works</a></li>
        <li class="header_menu--item"><a href="#contact" class="header_link">Contact</a></li>
      </ul>
      
      <button type="button" class="menu-btn" @click="toggleMenu">
        <img src="/src/assets/feather_menu.png" alt="menu">
      </button>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";

const menuOpen = ref(false);
const toggleMenu = () => {
  menuOpen.value = !menuOpen.value;
};
</script>

<style scoped>
a, button {
  color: inherit;
  text-decoration: none;
  list-style: none;
  border: none;
  background: none;
  cursor: pointer;
  font: inherit;
}

.header {
  background-color: #a200ff;
  padding: 15px 20px;
  box-shadow: 0 4px 15px rgba(231, 96, 255, 0.3);
  position: sticky;
  top: 0;
  z-index: 100;
}

.header_navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.logo {
  height: 50px;
}

.header_menu {
  display: flex;
  gap: 25px;
}

.header_menu--item {
  list-style: none;
}

.header_link {
  color: #fff;
  font-weight: 500;
  transition: all 0.3s ease;
  position: relative;
  padding: 5px 0;
  font-size: 19px;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

.header_link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -2px;
  width: 0%;
  height: 2px;
  background: #ffffff;
  transition: 0.3s;
}

.header_link:hover::after {
  width: 100%;
}

.menu-btn img {
  width: 28px;
  height: 28px;
  filter: invert(100%) sepia(0%) saturate(0%) hue-rotate(170deg) brightness(105%) contrast(105%);
}

@media (max-width: 900px) {
  .header_menu {
    display: none; 
    flex-direction: column;
    background: #f09bff;
    position: absolute;
    top: 70px;
    right: 20px;
    width: 200px;
    padding: 20px;
    border-radius: 10px;
  }

  .header_menu.show-menu {
    display: flex; 
  }

  .menu-btn {
    display: block;
  }
}
</style>
