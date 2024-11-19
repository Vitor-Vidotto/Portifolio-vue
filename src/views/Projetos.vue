<script setup lang="ts">
import ProjetosHeader from '../components/ProjetosHeader.vue'
import ProjetosContent from '../components/ProjetosContent.vue'
</script>

<template>
  <div class="projetos-page">
    <ProjetosHeader />
    <ProjetosContent />
  </div>
</template>

<style scoped>
.about-page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center; /* Centraliza o conteúdo horizontalmente */
  justify-content: center; /* Centraliza o conteúdo verticalmente */
  background-color: var(--color-background);
  color: var(--color-text);
}

.about-page > * {
  text-align: left; /* Garante que os itens internos não sejam centralizados */
}
</style>
