<template>
  <header class="header">
    <div class="container header_navbar">
      <a href="#" class="logo-wrapper">
        <img src="/src/assets/мah.png" alt="logo" class="logo" />
      </a>

     <ul :class="['header_menu', { 'show-menu': menuOpen }]">
  <li class="header_menu--item"><a href="#" class="header_link" @click.prevent="$emit('change-section', 'about')">About</a></li>
  <li class="header_menu--item"><a href="#" class="header_link" @click.prevent="$emit('change-section', 'works')">Works</a></li>
  <li class="header_menu--item"><a href="#" class="header_link" @click.prevent="$emit('change-section', 'contact')">Contact</a></li>
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
const toggleMenu = () => menuOpen.value = !menuOpen.value;
</script>

<style scoped>
ul{
  text-decoration: none; 
  list-style-type: none;
}
/* ===== GLOBAL RESET ===== */
a, button {
  color: inherit;
  text-decoration: none;
  border: none;
  background: none;
  cursor: pointer;
  font: inherit;
}

/* ===== HEADER ===== */
.header {
  background: rgba(10, 0, 41, 0.842);
  backdrop-filter: blur(18px);
  padding: 18px 22px;
  position: sticky;
  top: 0;
  z-index: 200;
  box-shadow: 0 0 25px rgba(100, 0, 255, 0.35);
  animation: headerFade 0.9s ease-out;
}

@keyframes headerFade {
  from { opacity: 0; transform: translateY(-20px); }
  to { opacity: 1; transform: translateY(0); }
}

.header_navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1250px;
  margin: 0 auto;
}

/* ===== LOGO ===== */
.logo-wrapper {
  display: flex;
  align-items: center;
  filter: drop-shadow(0 0 8px rgba(150, 0, 255, 0.6));
}

.logo {
  height: 58px;
  transition: transform 0.6s ease, filter 0.6s ease;
}

.logo-wrapper:hover .logo {
  transform: scale(1.08) rotate(1.5deg);
  filter: drop-shadow(0 0 15px rgba(180, 0, 255, 0.9));
}

/* ===== MENU (DESKTOP) ===== */
.header_menu {
  display: flex;
  gap: 35px;
}


.header_link {
  position: relative;
  color: #c8aaff;
  font-weight: 600;
  font-size: 20px;
  transition: 0.35s ease;
  letter-spacing: 1.1px;
  text-shadow: 0 0 4px rgba(130, 0, 255, 0.6);
}

/* glowing neon underline */
.header_link::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 50%;
  width: 0%;
  height: 2px;
  background: linear-gradient(45deg, #a45bff, #d68aff);
  transition: 0.4s ease;
  border-radius: 6px;
  transform: translateX(-50%);
  box-shadow: 0 0 6px rgba(200, 0, 255, 0.7);
}

.header_link:hover {
  color: #e5cfff;
  text-shadow: 0 0 8px rgba(200, 0, 255, 1);
}

.header_link:hover::after {
  width: 80%;
}

/* ===== MENU BUTTON ===== */
.menu-btn img {
  width: 32px;
  height: 32px;
  filter: invert(100%) drop-shadow(0 0 10px #a45bff);
  transition: 0.35s;
}

.menu-btn:hover img {
  transform: scale(1.18);
  filter: invert(100%) drop-shadow(0 0 15px #d68aff);
}

.menu-btn {
  display: none;
}

/* ===== MOBILE MENU ===== */
@media (max-width: 768px) {

  .menu-btn {
    display: block;
  }

  .header_menu {
    position: absolute;
    top: 80px;
    right: 25px;
    width: 230px;
    padding: 22px;
    flex-direction: column;
    gap: 20px;

    background: rgba(25, 0, 60, 0.75);
    border: 1px solid rgba(140, 0, 255, 0.3);
    border-radius: 14px;

    box-shadow: 0 0 30px rgba(160, 0, 255, 0.4),
                inset 0 0 20px rgba(90, 0, 160, 0.35);

    backdrop-filter: blur(18px);

    opacity: 0;
    transform: translateY(-12px);
    pointer-events: none;
    transition:
      opacity 0.4s ease,
      transform 0.4s ease;
  }

  .header_menu.show-menu {
    opacity: 1;
    transform: translateY(0);
    pointer-events: auto;
  }
}
</style>
