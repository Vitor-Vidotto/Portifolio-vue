<script setup>
import { ref } from 'vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'

// Referências para controle do estado de abertura de cada item
const isOpen1 = ref(false)
const isOpen2 = ref(false)
const isOpen3 = ref(false)
const isOpen4 = ref(false)

// Variáveis para o efeito de digitação
const words = ref(['Web', 'Desktop', 'Mobile']) // Palavras a serem digitadas
const currentWord = ref('') // Palavra atual que está sendo digitada
const wordIndex = ref(0) // Índice da palavra sendo exibida
const typing = ref(true) // Controle do modo de digitação/apagamento

// Função para alternar o estado de cada item
const toggleItem = (index) => {
  if (index === 1) {
    isOpen1.value = !isOpen1.value
    if (isOpen1.value) startTypingEffect() // Inicia o efeito ao abrir
  }
  if (index === 2) isOpen2.value = !isOpen2.value
  if (index === 3) isOpen3.value = !isOpen3.value
  if (index === 4) isOpen4.value = !isOpen4.value
}

// Função para iniciar o efeito de digitação
const startTypingEffect = () => {
  currentWord.value = ''
  wordIndex.value = 0
  typing.value = true
  typeWord() // Inicia o efeito de digitação
}

// Função para digitar uma palavra
const typeWord = () => {
  const word = words.value[wordIndex.value]
  if (typing.value) {
    currentWord.value += word.charAt(currentWord.value.length)
    if (currentWord.value.length === word.length) {
      setTimeout(() => {
        typing.value = false
        setTimeout(deleteWord, 1000)
      }, 1000)
    } else {
      setTimeout(typeWord, 100)
    }
  }
}

// Função para apagar a palavra digitada
const deleteWord = () => {
  if (currentWord.value.length > 0) {
    currentWord.value = currentWord.value.slice(0, -1)
    setTimeout(deleteWord, 100)
  } else {
    wordIndex.value = (wordIndex.value + 1) % words.value.length
    typing.value = true
    setTimeout(typeWord, 200)
  }
}
</script>

<template>
  <section class="about-content">

    <!-- Item 1 -->
    <div class="item" :class="{ open: isOpen1 }" @click="toggleItem(1)">
      <i>
        <CommunityIcon />
      </i>
      <div class="details">
        <h3>Quem Sou?</h3>
        <p v-if="isOpen1">
            <p>Me chamo Vitor Vidotto!</p>
          Sou desenvolvedor <span style="color: brown;">{{ currentWord }}</span>!
          <br />
        </p>
      </div>
    </div>

    <!-- Item 2 -->
    <div class="item" :class="{ open: isOpen2 }" @click="toggleItem(2)">
      <i>
        <ToolingIcon />
      </i>
      <div class="details">
        <h3>Estudos</h3>
        <p v-if="isOpen2">
          Estou me formando em Engenharia da Computação pela universidade
          <a href="https://facens.br" target="_blank" rel="noopener">Facens</a> 
          <br />
          Estou estudando CyberSegurança pela
          <a href="https://tryhackme.com/" target="_blank" rel="noopener">TryHackMe</a> 
          + 
          <a href="https://www.hackthebox.com" target="_blank" rel="noopener">HackTheBox</a>. 
          Se quiser conhecer mais sobre meus projetos e estudos, veja meu
          <a href="https://github.com/Vitor-Vidotto/" target="_blank" rel="noopener">GitHub</a> 
          !
        </p>
      </div>
    </div>

    <!-- Item 3 -->
    <div class="item" :class="{ open: isOpen3 }" @click="toggleItem(3)">
      <i>
        <EcosystemIcon />
      </i>
      <div class="details">
        <h3>Conhecimentos</h3>
        <p v-if="isOpen3">
          <strong>Frameworks:</strong>
        </p>
        <ul v-if="isOpen3">
          <li>Vue.js</li>
          <li>React</li>
          <li>Next.js</li>
          <li>Nuxt.js</li>
          <li>Express</li>
          <li>Electron</li>
          <li>Tauri</li>
          <li>Cypress</li>
          <li>Jest</li>
        </ul>

        <p v-if="isOpen3">
          <strong>Linguagens:</strong>
        </p>
        <ul v-if="isOpen3">
          <li>Python</li>
          <li>JavaScript</li>
          <li>TypeScript</li>
          <li>Rust</li>
          <li>C#</li>
          <li>Java</li>
        </ul>

        <p v-if="isOpen3">
          <strong>Idiomas:</strong>
        </p>
        <ul v-if="isOpen3">
          <li>Português - Nativo</li>
          <li>Inglês - Fluente</li>
          <li>Espanhol - Básico</li>
          <li>Alemão - Básico</li>
        </ul>

        <p v-if="isOpen3">
          <strong>Outros Conhecimentos:</strong>
        </p>
        <ul v-if="isOpen3">
          <li>Docker</li>
          <li>Kubernetes</li>
          <li>MongoDB</li>
          <li>PostgreSQL</li>
        </ul>
      </div>
    </div>

    <!-- Item 4 -->
    <div class="item" :class="{ open: isOpen4 }" @click="toggleItem(4)">
      <i>
        <SupportIcon />
      </i>
      <div class="details">
        <h3>Gostou?</h3>
        <p v-if="isOpen4">
          Entre em contato comigo na pagina
          <a href="/contato" rel="noopener">Contato</a>!
          <br />
          Você pode me ajudar favoritando esse repositório no meu
          <a href="https://github.com/Vitor-Vidotto/Portifolio-vue" target="_blank" rel="noopener">GitHub</a>!
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Estilos para a seção de conteúdo */
.about-content {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 2rem;
  width: 100%;
  max-width: 800px;
}

/* Estilos para os itens */
.item {
  display: flex;
  align-items: center;
  cursor: pointer;
  padding: 1rem;
  border: 1px solid var(--color-border);
  border-radius: 8px;
  background-color: var(--color-background-light);
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.item:hover {
  background-color: var(--color-background-hover);
  transform: scale(1.02);
}

i {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50px;
  height: 50px;
  border: 2px solid var(--color-border);
  border-radius: 50%;
  margin-right: 1rem;
  font-size: 1.5rem;
  flex-shrink: 0; /* Garante que o ícone não será redimensionado */
}

.details h3 {
  margin: 0;
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--color-heading);
}

.details p {
  margin: 0.5rem 0 0;
  font-size: 1rem;
  color: var(--color-text);
  line-height: 1.4;
}

.item.open p {
  animation: slideDown 0.3s ease forwards;
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Estilos personalizados para os ícones */
</style>
