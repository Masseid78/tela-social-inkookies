<script setup>
import { onMounted, ref } from 'vue'
import LinkCard from './LinkCard.vue'

const links = [
  {
    title: 'Ver Cookies',
    description: 'Conheça nossos sabores e faça seu pedido 🍪',
    href: 'https://instagram.com/inkookielab',
    icon: 'cookie',
  },
  {
    title: 'Cartão Fidelidade',
    description: 'Seja um dos primeiros assinantes! 🤎',
    href: 'https://instagram.com/inkookielab',
    icon: 'loyalty',
  },
  {
    title: 'Orçamento para Festas',
    description: 'Faça seu evento ainda mais doce e inesquecível! ✨',
    href: 'https://wa.me/5551999999999',
    icon: 'party',
  },
]

const infoItems = [
  { label: 'Cookies artesanais', icon: 'cookie' },
  { label: 'Santa Cruz do Sul/RS', icon: 'pin' },
  { label: 'Terça à sábado', icon: 'calendar' },
  { label: 'Encomendas pela DM', icon: 'mail' },
]

const socials = [
  {
    name: 'Instagram',
    href: 'https://instagram.com/inkookielab',
    icon: 'instagram',
  },
  {
    name: 'WhatsApp',
    href: 'https://wa.me/5551999999999',
    icon: 'whatsapp',
  },
  {
    name: 'Email',
    href: 'mailto:contato@inkookielab.com',
    icon: 'email',
  },
]

const loaded = ref(false)

function onReady() {
  loaded.value = true
}

onMounted(() => {
  // Garante animação mesmo se a imagem já estiver em cache
  requestAnimationFrame(() => {
    loaded.value = true
  })
})
</script>

<template>
  <div class="social" :class="{ 'social--ready': loaded }">
    <div class="social__bg" aria-hidden="true" />
    <div class="social__content">
      <header class="social__header">
        <div class="social__logo-wrap">
          <img
            class="social__logo"
            src="/images/logo.png"
            alt="Inkookie Lab"
            width="140"
            height="140"
            @load="onReady"
          />
        </div>
        <h1 class="social__title">Inkookie Lab 🍪</h1>
        <p class="social__tagline">A arte virou cookie e tá delicioso! 🤎</p>
      </header>

      <ul class="social__info" aria-label="Informações">
        <li v-for="item in infoItems" :key="item.label" class="social__info-item">
          <span class="social__info-icon" aria-hidden="true">
            <svg v-if="item.icon === 'cookie'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7">
              <circle cx="12" cy="12" r="9" />
              <circle cx="9" cy="10" r="1" fill="currentColor" stroke="none" />
              <circle cx="14" cy="9" r="1" fill="currentColor" stroke="none" />
              <circle cx="11" cy="14" r="1" fill="currentColor" stroke="none" />
              <circle cx="15.5" cy="13.5" r="1" fill="currentColor" stroke="none" />
            </svg>
            <svg v-else-if="item.icon === 'pin'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <path d="M12 21s7-5.4 7-11a7 7 0 1 0-14 0c0 5.6 7 11 7 11z" />
              <circle cx="12" cy="10" r="2.2" />
            </svg>
            <svg v-else-if="item.icon === 'calendar'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3.5" y="5" width="17" height="15" rx="2" />
              <path d="M8 3.5v3M16 3.5v3M3.5 10h17" />
            </svg>
            <svg v-else viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3" y="5.5" width="18" height="13" rx="2" />
              <path d="m4 7.5 8 6 8-6" />
            </svg>
          </span>
          <span class="social__info-label">{{ item.label }}</span>
        </li>
      </ul>

      <nav class="social__links" aria-label="Links principais">
        <LinkCard
          v-for="link in links"
          :key="link.title"
          :title="link.title"
          :description="link.description"
          :href="link.href"
        >
          <template #icon>
            <svg v-if="link.icon === 'cookie'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8">
              <path d="M12 3.5a8.5 8.5 0 1 0 8.3 10.4A4.2 4.2 0 0 1 12 3.5z" />
              <circle cx="9" cy="11" r="1" fill="currentColor" stroke="none" />
              <circle cx="13.5" cy="9.5" r="1" fill="currentColor" stroke="none" />
              <circle cx="11.5" cy="15" r="1" fill="currentColor" stroke="none" />
              <circle cx="15.5" cy="14" r="1" fill="currentColor" stroke="none" />
            </svg>
            <svg v-else-if="link.icon === 'loyalty'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3" y="6" width="18" height="12" rx="2.2" />
              <path d="M3 10h18" />
              <path d="m14.2 13.2 1 .7-.3-1.2.9-.8-1.2-.1-.4-1.1-.4 1.1-1.2.1.9.8-.3 1.2z" fill="currentColor" stroke="none" />
            </svg>
            <svg v-else viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
              <path d="M6 15c2.2-.3 4.2-1.6 5-3.8.8 2.2 2.8 3.5 5 3.8-2.2.3-4.2 1.6-5 3.8-.8-2.2-2.8-3.5-5-3.8z" />
              <path d="M14.5 7.5 16 4l1.2 2.8L20 8l-2.8 1.1L16 12l-1.1-2.9L12 8l2.5-.5z" />
              <path d="m5 8 .7-1.6L7.5 6l-1.6.4L5 8l-.4-1.6L3 6l1.6-.4z" />
            </svg>
          </template>
        </LinkCard>
      </nav>

      <footer class="social__footer">
        <p class="social__closing">Feito com amor para adoçar seu dia! ♡</p>

        <div class="social__socials">
          <a
            v-for="social in socials"
            :key="social.name"
            :href="social.href"
            class="social__social"
            :aria-label="social.name"
            target="_blank"
            rel="noopener noreferrer"
          >
            <svg v-if="social.icon === 'instagram'" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7">
              <rect x="3.5" y="3.5" width="17" height="17" rx="5" />
              <circle cx="12" cy="12" r="4" />
              <circle cx="17.2" cy="6.8" r="1" fill="currentColor" stroke="none" />
            </svg>
            <svg v-else-if="social.icon === 'whatsapp'" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 3.2a8.3 8.3 0 0 0-7.2 12.5L4 20.8l5.3-.8A8.3 8.3 0 1 0 12 3.2zm0 15.1a6.8 6.8 0 0 1-3.5-1l-.2-.1-3.2.5.5-3.1-.1-.3a6.8 6.8 0 1 1 6.5 4zm3.9-5.1c-.2-.1-1.3-.6-1.5-.7-.2-.1-.4-.1-.5.1-.2.2-.6.7-.7.9-.1.1-.3.2-.5.1-.2-.1-1-.4-1.9-1.2-.7-.6-1.2-1.4-1.3-1.6-.1-.2 0-.4.1-.5l.4-.4c.1-.1.2-.3.2-.4.1-.2 0-.3 0-.4 0-.1-.5-1.3-.7-1.8-.2-.5-.4-.4-.5-.4h-.5c-.2 0-.4.1-.6.3-.2.2-.8.8-.8 1.9s.8 2.2.9 2.3c.1.2 1.6 2.5 3.9 3.4 1.5.6 2 .5 2.7.4.4-.1 1.3-.5 1.5-1 .2-.5.2-.9.1-1 0-.1-.2-.2-.4-.3z" />
            </svg>
            <svg v-else viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round">
              <rect x="3" y="5.5" width="18" height="13" rx="2" />
              <path d="m4 7.5 8 6 8-6" />
            </svg>
          </a>
        </div>

        <p class="social__handle">@inkookielab</p>
      </footer>
    </div>
  </div>
</template>

<style scoped>
.social {
  position: relative;
  min-height: 100svh;
  width: 100%;
  overflow: hidden;
  color: #4a3228;
  isolation: isolate;
}

.social__bg {
  position: fixed;
  inset: 0;
  z-index: -1;
  background-color: #f7efe6;
  background-image: url('/images/background.png');
  background-position: center top;
  background-repeat: no-repeat;
  background-size: cover;
}

.social__content {
  position: relative;
  z-index: 1;
  width: min(100%, 28rem);
  margin: 0 auto;
  padding: 2.4rem 1.35rem 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.35rem;
  opacity: 0;
  transform: translateY(10px);
  transition: opacity 0.45s ease, transform 0.45s ease;
}

.social--ready .social__content {
  opacity: 1;
  transform: translateY(0);
}

.social__header {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 0.55rem;
  animation: rise 0.55s ease both;
}

.social__logo-wrap {
  width: 7.5rem;
  height: 7.5rem;
  border-radius: 50%;
  padding: 0.2rem;
  background: linear-gradient(145deg, #f3e2d2, #fffaf4);
  border: 2px solid #7a5440;
  box-shadow: 0 8px 22px rgba(74, 50, 40, 0.12);
  overflow: hidden;
  display: grid;
  place-items: center;
  animation: pop 0.65s cubic-bezier(0.22, 1, 0.36, 1) both;
}

.social__logo {
  width: 108%;
  height: 108%;
  object-fit: cover;
  display: block;
}

.social__title {
  margin: 0.35rem 0 0;
  font-family: 'Poppins', sans-serif;
  font-weight: 700;
  font-size: 1.55rem;
  letter-spacing: -0.02em;
  color: #4a3228;
}

.social__tagline {
  margin: 0;
  font-family: 'Poppins', sans-serif;
  font-weight: 400;
  font-size: 0.92rem;
  color: #6d4a38;
  line-height: 1.4;
}

.social__info {
  list-style: none;
  margin: 0.15rem 0 0;
  padding: 0;
  width: 100%;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0.4rem;
  animation: rise 0.6s ease 0.08s both;
}

.social__info-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  text-align: center;
}

.social__info-icon {
  color: #6d4a38;
  display: grid;
  place-items: center;
}

.social__info-icon svg {
  width: 1.35rem;
  height: 1.35rem;
}

.social__info-label {
  font-family: 'Poppins', sans-serif;
  font-size: 0.58rem;
  font-weight: 500;
  line-height: 1.25;
  color: #6d4a38;
}

.social__links {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  animation: rise 0.65s ease 0.14s both;
}

.social__footer {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.85rem;
  margin-top: 0.35rem;
  animation: rise 0.7s ease 0.2s both;
}

.social__closing {
  margin: 0;
  font-family: 'Dancing Script', cursive;
  font-size: 1.25rem;
  font-weight: 600;
  color: #5a3d2b;
  text-align: center;
}

.social__socials {
  display: flex;
  align-items: center;
  gap: 0.85rem;
}

.social__social {
  width: 2.35rem;
  height: 2.35rem;
  border-radius: 50%;
  display: grid;
  place-items: center;
  color: #5a3d2b;
  background: rgba(255, 250, 244, 0.85);
  border: 1.5px solid rgba(122, 84, 58, 0.35);
  transition: transform 0.2s ease, background 0.2s ease;
}

.social__social:hover {
  transform: translateY(-2px) scale(1.05);
  background: #fffaf4;
}

.social__social svg {
  width: 1.15rem;
  height: 1.15rem;
}

.social__handle {
  margin: 0;
  font-family: 'Poppins', sans-serif;
  font-size: 0.8rem;
  font-weight: 500;
  color: #6d4a38;
  letter-spacing: 0.02em;
}

@keyframes rise {
  from {
    opacity: 0;
    transform: translateY(14px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes pop {
  from {
    opacity: 0;
    transform: scale(0.86);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

@media (max-width: 380px) {
  .social__content {
    padding-inline: 1rem;
  }

  .social__title {
    font-size: 1.35rem;
  }

  .social__info-label {
    font-size: 0.54rem;
  }
}

@media (min-width: 768px) {
  .social__bg {
    background-size: cover;
    background-position: center;
  }

  .social__content {
    padding-top: 3rem;
    padding-bottom: 3rem;
  }

  .social__logo-wrap {
    width: 8.25rem;
    height: 8.25rem;
  }
}
</style>
