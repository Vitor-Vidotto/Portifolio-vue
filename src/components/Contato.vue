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
    <a href="https://wa.me/5515992609453?text=Ol%C3%A1%2C%20tudo%20bem%3F%20Estou%20entrando%20em%20contato%20pois%20visitei%20seu%20portif%C3%B3lio!" target="_blank" rel="noopener">Entre em contato</a>
    em uma conversa direta.
  </ContatoItem>

  <ContatoItem>
    <template #icon>
      <LinkedInIcon />
    </template>
    <template #heading>LinkedIn</template>
    <a href="linkedin.com/in/vitor-vidotto/" target="_blank" rel="noopener">Entre em contato</a>
    para propostas diretas.
  </ContatoItem>
  
  <ContatoItem>
    <template #icon>
      <InstagramIcon />
    </template>
    <template #heading>Instagram</template>
    <a href="https://www.instagram.com/soy.vidotto/" target="_blank" rel="noopener">Entre em contato</a>
    pelo instagram para parcerias.
  </ContatoItem>
</template>
