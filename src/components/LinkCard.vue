<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
  href: {
    type: String,
    default: '#',
  },
})
</script>

<template>
  <a :href="href" class="link-card" target="_blank" rel="noopener noreferrer">
    <span class="link-card__icon" aria-hidden="true">
      <slot name="icon" />
    </span>
    <span class="link-card__text">
      <span class="link-card__title">{{ title }}</span>
      <span class="link-card__desc">{{ description }}</span>
    </span>
    <span class="link-card__arrow" aria-hidden="true">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M9 6l6 6-6 6" />
      </svg>
    </span>
  </a>
</template>

<style scoped>
.link-card {
  display: flex;
  align-items: center;
  gap: 0.85rem;
  width: 100%;
  padding: 0.9rem 1rem;
  border-radius: 1.1rem;
  background: rgba(255, 252, 248, 0.92);
  border: 1px solid rgba(122, 84, 58, 0.12);
  box-shadow: 0 6px 18px rgba(74, 50, 40, 0.08);
  text-decoration: none;
  color: inherit;
  transition: transform 0.2s ease, box-shadow 0.2s ease, background 0.2s ease;
}

.link-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 24px rgba(74, 50, 40, 0.12);
  background: #fffdf9;
}

.link-card:active {
  transform: translateY(0);
}

.link-card__icon {
  flex-shrink: 0;
  display: grid;
  place-items: center;
  width: 2.75rem;
  height: 2.75rem;
  border-radius: 50%;
  background: #f0e0d0;
  color: #5a3d2b;
}

.link-card__icon :deep(svg) {
  width: 1.35rem;
  height: 1.35rem;
}

.link-card__text {
  flex: 1;
  min-width: 0;
  display: flex;
  flex-direction: column;
  gap: 0.15rem;
  text-align: left;
}

.link-card__title {
  font-family: 'Poppins', sans-serif;
  font-weight: 700;
  font-size: 0.98rem;
  color: #4a3228;
  line-height: 1.2;
}

.link-card__desc {
  font-family: 'Poppins', sans-serif;
  font-weight: 400;
  font-size: 0.72rem;
  color: #7a5440;
  line-height: 1.35;
}

.link-card__arrow {
  flex-shrink: 0;
  color: #8b634c;
  opacity: 0.75;
}

.link-card__arrow svg {
  width: 1.15rem;
  height: 1.15rem;
  display: block;
}
</style>
