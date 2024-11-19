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
.projetos-page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center; /* Centraliza o conteúdo horizontalmente */
  justify-content: center; /* Centraliza o conteúdo verticalmente */
  background-color: var(--color-background);
  color: var(--color-text);
}

.projetos-page > * {
  text-align: left; /* Garante que os itens internos não sejam centralizados */
}
</style>
