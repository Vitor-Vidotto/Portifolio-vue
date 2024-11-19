<script setup lang="ts">
import ContatoItem from './ContatoItem.vue'
import WhatsAppIcon from './icons/IconWhatsApp.vue'
import InstagramIcon from './icons/IconInstagram.vue'
import LinkedInIcon from './icons/IconLinkedIn.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>

<template>
  <ContatoItem>
    <template #icon>
      <WhatsAppIcon />
    </template>
    <template #heading>WhatsApp</template>
    <a href="https://vuejs.org/" target="_blank" rel="noopener">Entre em contato</a>
    em uma conversa direta.
  </ContatoItem>

  <ContatoItem>
    <template #icon>
      <LinkedInIcon />
    </template>
    <template #heading>LinkedIn</template>
    <a href="https://vuejs.org/" target="_blank" rel="noopener">Entre em contato</a>
    para propostas diretas.
  </ContatoItem>
  
  <ContatoItem>
    <template #icon>
      <InstagramIcon />
    </template>
    <template #heading>Instagram</template>
    <a href="https://vuejs.org/" target="_blank" rel="noopener">Entre em contato</a>
    pelo instagram para parcerias.
  </ContatoItem>
</template>
