<template>
  <section class="section">
    <div class="container">
      <button class="section-btn" @click="toggle = !toggle">
        {{ title }}
      </button>
      <div v-if="toggle" class="section-content">
        <slot></slot>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
const props = defineProps({ title: String });
const toggle = ref(false);
</script>

<style scoped>
.section {
  margin-bottom: 40px;
}

.section-btn {
  width: 100%;
  padding: 18px 25px;
  font-size: 1.3em;
  background-color: #7b1fa2;
  color: white;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  transition: background 0.3s;
}

.section-btn:hover {
  background-color: #5e0d86;
}

.section-content {
  margin-top: 20px;
  padding: 25px;
  background: #f3e5f5;
  border-radius: 15px;
  box-shadow: 0 6px 15px rgba(0,0,0,0.1);
  transition: all 0.3s;
}
</style>
