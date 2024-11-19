<template> 
  <div class="contato-item">
    <div class="hover-area">
      <i>
        <slot name="icon"></slot>
      </i>
      <div class="details">
        <h3>
          <slot name="heading"></slot>
        </h3>
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Estilo base para ContatoItem */
.contato-item {
  margin-top: 2rem;
  display: flex;
  align-items: center; /* Alinha os itens verticalmente */
  position: relative;
  padding: 1rem 1.5rem; /* Ajuste para maior espaçamento interno */
  border-radius: 8px;
  overflow: hidden;
  background: var(--color-background);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.contato-item:hover {
  transform: translateY(-5px); /* Efeito de flutuar */
}

/* Área de hover que abrange o ícone e o texto */
.hover-area {
  display: flex;
  align-items: center;
  position: relative;
  width: 100%;
}

.hover-area:hover::before {
  transform: translate(-50%, -50%) scale(1.2);
  opacity: 1;
}

/* Detalhes */
.details {
  flex: 1;
  margin-left: 2rem; /* Aumenta a distância entre o ícone e o texto */
}

i {
  display: flex;
  place-items: center;
  place-content: center;
  width: 50px; /* Ícone maior */
  height: 50px;
  color: var(--color-text);
  background: var(--color-background);
  border-radius: 50%;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, filter 0.3s ease;
  margin-top: 10px; /* Adiciona margem superior */
}

/* Efeito de hover no ícone, ativado pelo hover na área maior */
.hover-area:hover i {
  transform: scale(1.1);
  filter: drop-shadow(0px 4px 6px rgba(255, 255, 255, 0.3));
}

/* Título */
h3 {
  font-size: 1.2rem;
  font-weight: 500;
  margin-bottom: 0.4rem;
  color: var(--color-heading);
}

/* Estilo responsivo */
@media (min-width: 1024px) {
  .contato-item {
    margin-top: 0;
    padding: 1rem 2rem; /* Maior espaçamento interno para desktops */
  }

  i {
    top: 50%;
    left: 0;
    position: relative;
    transform: translateY(-30%); /* Reposiciona um pouco mais abaixo */
    border: none; /* Remoção de borda no modo desktop */
    background: var(--color-background);
  }

  .details {
    margin-left: 2.5rem; /* Alinhamento mais espaçado no desktop */
  }
}
</style>
