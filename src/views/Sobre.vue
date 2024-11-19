<script setup lang="ts">
import AboutHeader from '../components/AboutHeader.vue'
import AboutContent from '../components/AboutContent.vue'
</script>

<template>
  <div class="about-page">
    <AboutHeader />
    <AboutContent />
  </div>
</template>

<style scoped>
.about-page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: var(--color-background);
  color: var(--color-text);
}
</style>
