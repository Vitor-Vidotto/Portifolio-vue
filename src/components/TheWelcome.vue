<script setup lang="ts">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Meu nome é Vitor Vidotto</template>
    Sou desenvolvedor full-stack e estudante de Engenharia da Computação, com experiência em tecnologias web, mobile e infraestrutura.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Programador & DevOps</template>

    Trabalho com desenvolvimento de soluções escaláveis e automatização de processos, além de atuar com práticas de DevOps para garantir ambientes estáveis.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <EcosystemIcon />
    </template>
    <template #heading>Entusiasta em CyberSegurança</template>
    Tenho interesse em cibersegurança e estou sempre buscando aprender novas técnicas para proteger sistemas e dados.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CommunityIcon />
    </template>
    <template #heading>Sempre em busca de aprender</template>

    Acredito no aprendizado contínuo e participo de comunidades para compartilhar e adquirir conhecimento.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <SupportIcon />
    </template>
    <template #heading>Deixe um FeedBack</template>

    Seu feedback é importante! Ajuda a melhorar e evoluir meu trabalho. Fique à vontade para compartilhar sua opinião.
  </WelcomeItem>
</template>
