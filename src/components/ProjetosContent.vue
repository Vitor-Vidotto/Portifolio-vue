<script setup>
import { ref, computed } from 'vue';

// Dados dos projetos com a URL da imagem atualizada
const projectsData = [
  {
    id: 1,
    title: "Aplicativo de listagem de filmes",
    description: "Uma aplicação onde o usuário pode ver os filmes disponíveis e ler a descrição.",
    image: "https://developers.elementor.com/docs/assets/img/elementor-placeholder-image.png",
    tag: ["Todos", "Celular"],
    gitUrl: "https://github.com/Vitor-Vidotto/FavMovies",
    previewUrl: "https://github.com/Vitor-Vidotto/FavMovies",
  },
  {
    id: 2,
    title: "App de Controle C#",
    description: "Desenvolvi um projeto em c# para monitorar e enviar arquivos via FTP.",
    image: "https://developers.elementor.com/docs/assets/img/elementor-placeholder-image.png",
    tag: ["Todos", "Desktop"],
    gitUrl: "https://github.com/Vitor-Vidotto",
    previewUrl: "https://github.com/Vitor-Vidotto",
  },
  {
    id: 3,
    title: "Portifólio Digital",
    description: "Meu primeiro portifólio digital feito em Angular.",
    image: "https://developers.elementor.com/docs/assets/img/elementor-placeholder-image.png",
    tag: ["Todos", "Web"],
    gitUrl: "https://github.com/Vitor-Vidotto/Portifolio",
    previewUrl: "https://vitor-vidotto.github.io/Portifolio/",
  },
  {
    id: 4,
    title: "Protótipo de site empresarial",
    description: "Desenvolvi um protótipo para um restaurante.",
    image: "https://developers.elementor.com/docs/assets/img/elementor-placeholder-image.png",
    tag: ["Todos", "Web"],
    gitUrl: "https://github.com/AutomatizaLabs/AutomatizaLabs",
    previewUrl: "https://github.com/AutomatizaLabs/AutomatizaLabs",
  },
  {
    id: 5,
    title: "Automações em Python",
    description: "Desenvolvi automações para processos de empresas em Python.",
    image: "https://developers.elementor.com/docs/assets/img/elementor-placeholder-image.png",
    tag: ["Todos", "Desktop"],
    gitUrl: "https://github.com/Vitor-Vidotto/python-automations",
    previewUrl: "https://github.com/Vitor-Vidotto/python-automations",
  },
];

// Estado da tag filtrada
const tag = ref("Todos");
const currentPage = ref(1);
const projectsPerPage = 2;

// Filtrando os projetos conforme a tag selecionada
const filteredProjects = computed(() => {
  return projectsData.filter(project => project.tag.includes(tag.value));
});

// Calculando os projetos a serem exibidos na página atual
const paginatedProjects = computed(() => {
  const start = (currentPage.value - 1) * projectsPerPage;
  const end = start + projectsPerPage;
  return filteredProjects.value.slice(start, end);
});

// Total de páginas
const totalPages = computed(() => {
  return Math.ceil(filteredProjects.value.length / projectsPerPage);
});

// Função para mudar a tag
const handleTagChange = (newTag) => {
  tag.value = newTag;
  currentPage.value = 1; // Resetar para a primeira página ao mudar a tag
};

// Funções para navegação de páginas
const goToPage = (page) => {
  if (page > 0 && page <= totalPages.value) {
    currentPage.value = page;
  }
};

const nextPage = () => {
  if (currentPage.value < totalPages.value) {
    currentPage.value++;
  }
};

const prevPage = () => {
  if (currentPage.value > 1) {
    currentPage.value--;
  }
};
</script>

<template>
  <section id="projects" class="px-4">
    <div class="text-white flex flex-wrap justify-center items-center gap-4 py-6 mb-6 w-full">
  <button @click="handleTagChange('Todos')" :class="{'bg-green-500': tag === 'Todos'}">Todos</button>
  <button @click="handleTagChange('Web')" :class="{'bg-green-500': tag === 'Web'}">Web</button>
  <button @click="handleTagChange('Celular')" :class="{'bg-green-500': tag === 'Celular'}">Celular</button>
  <button @click="handleTagChange('Desktop')" :class="{'bg-green-500': tag === 'Desktop'}">Desktop</button>
</div>


    <ul class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8 md:gap-12">
      <li v-for="(project, index) in paginatedProjects" :key="index" class="card">
        <img :src="project.image" alt="Imagem do Projeto" class="card-image" />
        <div class="card-content">
          <h3 class="card-title">{{ project.title }}</h3>
          <p class="card-text">{{ project.description }}</p>
          <div class="card-actions">
            <a :href="project.gitUrl" target="_blank" class="card-button">GitHub</a>
            <a :href="project.previewUrl" target="_blank" class="card-button">Visualizar</a>
          </div>
        </div>
      </li>
    </ul>

    <!-- Paginação -->
    <div class="flex justify-center gap-4 mt-6">
      <button @click="prevPage" :disabled="currentPage === 1" class="pagination-button"><</button>
      <span class="text-white">{{ currentPage }} de {{ totalPages }}</span>
      <button @click="nextPage" :disabled="currentPage === totalPages" class="pagination-button">></button>
    </div>
  </section>
</template>

<style scoped>
.card {
  border: 2px solid #ddd;
  border-radius: 12px;
  background-color: #fff;
  overflow: hidden;
  width: 300px; /* Define a largura fixa do card */
  height: 500px; /* Define a altura fixa do card */
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column; /* Garante que o conteúdo seja empilhado verticalmente */
}

.card:hover {
  transform: scale(1.05);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
}

.card-image {
  width: 100%;
  height: 200px; /* Define a altura fixa da imagem */
  object-fit: cover;
  border-bottom: 2px solid #f1f1f1;
}

.card-content {
  padding: 20px;
  flex-grow: 1; /* Permite que o conteúdo ocupe o espaço restante */
}

.card-title {
  font-size: 1.75rem;
  font-weight: bold;
  color: #333;
  margin-bottom: 12px;
}

.card-text {
  font-size: 1rem;
  color: #666;
  margin-bottom: 16px;
}

.card-actions {
  display: flex;
  justify-content: space-between; /* Garante que os botões fiquem no final */
  margin-top: auto; /* Faz os botões se moverem para o final do card */
  padding: 12px;
}

.card-button {
  padding: 10px 20px;
  background-color: #2d2d2d; /* Preto */
  color: #fff;
  border-radius: 4px;
  text-decoration: none;
  font-size: 1rem;
  text-align: center;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.card-button:hover {
  background-color: #004d2c; /* Verde escuro */
  transform: translateY(-2px);
}

.card-actions a {
  padding: 10px 20px;
  background-color: #2d2d2d; /* Preto */
  color: white;
  border-radius: 4px;
  text-decoration: none;
  font-size: 1rem;
  text-align: center;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.card-actions a:hover {
  background-color: #004d2c; /* Verde escuro */
  transform: translateY(-2px);
}



/* Estilos dos botões de filtro */
button {
  padding: 10px 20px;
  background-color: #006603; /* Verde */
  color: #fff;
  border: 2px solid #006603;
  border-radius: 6px;
  font-size: 1rem;
  font-weight: bold;
  margin-bottom: 20px;
  margin-right: 10px;
  align-self: center;
  cursor: pointer;
  transition: all 0.3s ease;
}

button:hover {
  background-color: #388e3c; /* Verde escuro */
  border-color: #388e3c;
}

button.bg-green-500 {
  background-color: #4caf50;
  color: white;
  border-color: #4caf50;
}

button.bg-green-500:hover {
  background-color: #388e3c;
}

/* Layout da seção */
/* Estilo da div de botões */
/* Estilo da div de botões */
#projects .text-white {
  display: flex;
  flex-wrap: wrap;
  justify-content: center; /* Alinha os botões ao centro */
  align-items: center;
  gap: 4px;
  padding: 6px 0;
  margin-bottom: 6px;
  width: 100%;
}
/* Estilo da div de navegação da paginação */
#projects .flex {
  display: flex;
  justify-content: center; /* Centraliza os botões */
  gap: 4px;
  margin-top: 1.5rem; /* Distância superior */
  margin-left: 20px; /* Ajusta para mover os botões ligeiramente para a direita */
}

/* Estilo dos botões de navegação da paginação */
.pagination-button {
  padding: 10px 20px;
  background-color: #006603;
  color: #fff;
  border: none;
  border-radius: 6px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
  width: 40px; /* Ajuste o tamanho dos botões */
  text-align: center; /* Garante que o conteúdo fique centralizado */
}

/* Efeito ao passar o mouse */
.pagination-button:hover {
  background-color: #388e3c;
}

/* Desabilita o botão */
.pagination-button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}


h2 {
  font-size: 2.5rem;
  font-weight: bold;
  color: #333;
  text-align: center;
  margin-bottom: 20px;
}

ul {
  display: grid;
  grid-template-columns: repeat(2, 1fr); /* Garante 2 colunas */
  gap: 20px;
}

/* Adaptação para dispositivos menores */
@media (max-width: 768px) {
  ul {
    grid-template-columns: 1fr 1fr; /* Garante 2 colunas até telas médias */
  }
}

@media (max-width: 480px) {
  ul {
    grid-template-columns: 1fr; /* Ajusta para 1 coluna em telas pequenas */
  }
}

/* Estilo da paginação */
.pagination-button {
  padding: 10px 20px;
  background-color: #006603;
  color: #fff;
  border: none;
  border-radius: 6px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.pagination-button:hover {
  background-color: #388e3c;
}

.pagination-button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}
</style>
