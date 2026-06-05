<script setup lang="ts">
import { ref, watchEffect, onMounted } from 'vue'

const theme = ref<'dark' | 'light'>('dark')
const toggleTheme = () => {
  theme.value = theme.value === 'dark' ? 'light' : 'dark'
}

const applyTheme = (mode: 'dark' | 'light') => {
  document.documentElement.classList.toggle('light', mode === 'light')
}

onMounted(() => {
  applyTheme(theme.value)
})

watchEffect(() => {
  applyTheme(theme.value)
})
</script>

<template>
  <div class="page-shell">
    <div class="card">
      <button class="theme-toggle" @click="toggleTheme">
        {{ theme === 'dark' ? 'Light mode' : 'Dark mode' }}
      </button>

      <div class="profile">
        <div class="avatar" aria-hidden="true"></div>
        <div class="copy">
          <h1>Randy Ollins</h1>
          <p>Building clean link-in-bio experiences that feel polished and personal.</p>
        </div>
      </div>

      <div class="links">
        <a href="https://portfolio.randyollins.com" target="_blank" rel="noreferrer">Portfolio</a>
        <a href="https://dribbble.com/randyollins" target="_blank" rel="noreferrer">Dribbble</a>
        <a href="https://linkedin.com/in/randyollins" target="_blank" rel="noreferrer">LinkedIn</a>
        <a href="mailto:hello@randyollins.com">Email</a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.page-shell {
  min-height: 100vh;
  display: grid;
  place-items: center;
  padding: 2rem 1.25rem;
  background: radial-gradient(circle at top, rgba(255, 255, 255, 0.08), transparent 32%), var(--color-background);
}

.card {
  width: min(100%, 480px);
  background: var(--color-background-soft);
  border: 1px solid var(--color-border);
  border-radius: 32px;
  box-shadow: 0 28px 80px rgba(0, 0, 0, 0.28);
  padding: 2.25rem;
  position: relative;
}

.theme-toggle {
  position: absolute;
  right: 1.3rem;
  top: 1.3rem;
  border: 1px solid rgba(255, 255, 255, 0.12);
  background: rgba(255, 255, 255, 0.05);
  color: var(--color-heading);
  font-size: 0.9rem;
  font-weight: 600;
  border-radius: 999px;
  padding: 0.75rem 1rem;
  cursor: pointer;
  transition: transform 0.25s ease, background-color 0.25s ease;
}

.theme-toggle:hover {
  transform: translateY(-1px);
  background: rgba(255, 255, 255, 0.12);
}

.profile {
  display: grid;
  gap: 1.5rem;
  place-items: center;
  text-align: center;
  margin-bottom: 2rem;
}

.avatar {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  border: 1px solid rgba(255, 255, 255, 0.12);
  background: linear-gradient(135deg, #5b8cff, #8f5bff);
  box-shadow: inset 0 0 0 2px rgba(255, 255, 255, 0.05);
}

.copy h1 {
  font-size: clamp(2rem, 2.5vw, 2.5rem);
  margin-bottom: 0.55rem;
  letter-spacing: -0.03em;
}

.copy p {
  color: var(--color-text);
  line-height: 1.8;
  max-width: 36rem;
}

.links {
  display: grid;
  gap: 1rem;
}

.links a {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 1rem 1.1rem;
  border-radius: 18px;
  border: 1px solid transparent;
  text-decoration: none;
  font-weight: 600;
  color: var(--color-button-text);
  background: var(--color-button);
  box-shadow: 0 20px 45px rgba(0, 0, 0, 0.18);
  transition: transform 0.25s ease, background-color 0.25s ease, border-color 0.25s ease;
}

.links a:hover {
  transform: translateY(-2px);
  background: var(--color-button-hover);
  border-color: rgba(255, 255, 255, 0.16);
}

.links a:nth-child(1) {
  background: linear-gradient(135deg, #7c5cff, #3bb2ff);
  color: #fff;
}

.links a:nth-child(1):hover {
  background: linear-gradient(135deg, #8f72ff, #56c8ff);
}

@media (max-width: 420px) {
  .card {
    padding: 1.75rem;
  }

  .theme-toggle {
    top: 1rem;
    right: 1rem;
  }
}
</style>
