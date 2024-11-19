<script setup>
</script>

<template>
  <header class="Projetos-header">
    <h1>Projetos</h1>
  </header>
</template>

<style scoped>
.Projetos-header {
  text-align: center;
  margin-top: 2rem;
  opacity: 0;
  animation: fadeIn 1.5s ease forwards;
}

.Projetos-header h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: var(--color-primary);
}

.Projetos-header p {
  font-size: 1.2rem;
  color: var(--color-secondary);
}

/* Animação */
@keyframes fadeIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
  from {
    opacity: 0;
    transform: translateY(30px);
  }
}
</style>
