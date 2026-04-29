<template>

   <!-- Mobile Menu Button -->
  <button
    class="md:hidden fixed top-4 left-4 z-50 bg-black text-white p-2 rounded"
    @click="isOpen = !isOpen"
  >
    ☰
  </button>

  <!-- Overlay -->
  <div
    v-if="isOpen"
    class="fixed inset-0 bg-black/50 z-40 md:hidden"
    @click="isOpen = false"
  ></div> 
  <nav class="sidebar transform transition-transform duration-300 md:translate-x-0"
  :class="isOpen ? 'translate-x-0' : '-translate-x-full'">
    <div class="logo-wrap">
      <div class="logo-box">
        <span class="logo-letter">P</span>
      </div>
      <p class="logo-name">Pooja</p>
      <p class="logo-role">Frontend Developer</p>
    </div>

    <ul class="nav-links">
      <li v-for="item in navItems" :key="item.label">
        <a
            :href="item.href"
            class="nav-link"
            :class="{ active: activeSection === item.label }"
            @click="setActive(item.label)"
        >
            {{ item.label }}
        </a>
      </li>
    </ul>

    <div class="socials">
      <a href="https://www.linkedin.com/in/pooja-chandrikapure-98b117220" class="social-icon" aria-label="LinkedIn">
        <svg viewBox="0 0 24 24" fill="currentColor" width="18" height="18">
          <path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/>
          <rect x="2" y="9" width="4" height="12"/>
          <circle cx="4" cy="4" r="2"/>
        </svg>
      </a>
      <a href="https://github.com/pooja-chandrikapure" class="social-icon" aria-label="GitHub">
        <svg viewBox="0 0 24 24" fill="currentColor" width="18" height="18">
          <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/>
        </svg>
      </a>
      <a href="mailto:poojachandrikapure3011@gmail.com" class="social-icon" aria-label="Email">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="18" height="18">
          <rect x="2" y="4" width="20" height="16" rx="2"/>
          <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/>
        </svg>
      </a>
    </div>

    <!-- <div class="scroll-hint">
      <span class="scroll-text">scroll down</span>
      <div class="scroll-arrow">↓</div>
    </div> -->
  </nav>
</template>

<script setup>
import { ref } from 'vue'

const isOpen = ref(false)
const navItems = [
  { label: 'About',    href: '#about' },
  { label: 'My Skills', href: '#skills' },
  { label: 'Work',     href: '#work' },
  { label: 'Contact',  href: '#contact' },
  { label: 'Blog',     href: '#blog' },
]

const activeSection = ref('Blog')
function setActive(label) { activeSection.value = label }
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&display=swap');

.sidebar {
  position: fixed;
  top: 0; left: 0;
  width: 140px;
  height: 100vh;
  background: #0d0d0d;
  border-right: 1px solid rgba(255,255,255,0.06);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem 0;
  z-index: 100;
  font-family: 'Space Mono', monospace;
}

.logo-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 3rem;
}

.logo-box {
  width: 70px;
  height: 70px;
  background: #111;
  border: 1px solid rgba(255,255,255,0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 0.5rem;
  position: relative;
  overflow: hidden;
}

.logo-box::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(128,0,128,0.2) 0%, rgba(255,66,117,0.15) 100%);
}

.logo-letter {
  font-size: 2rem;
  font-weight: 700;
  background: linear-gradient(135deg, #800080, #ebaeeb);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  position: relative;
  z-index: 1;
}

.logo-name {
  color: #fff;
  font-size: 0.85rem;
  font-weight: 700;
  margin: 0;
  letter-spacing: 0.05em;
}

.logo-role {
  color: #666;
  font-size: 0.65rem;
  margin: 0.2rem 0 0;
  letter-spacing: 0.04em;
}

.nav-links {
  list-style: none;
  padding: 0; margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
  width: 100%;
  align-items: center;
}

.nav-link {
  display: block;
  color: #888;
  text-decoration: none;
  font-size: 0.72rem;
  letter-spacing: 0.04em;
  padding: 0.5rem 1rem;
  transition: color 0.2s ease;
  text-align: center;
  width: 100%;
}

.nav-link:hover { color: #ccc; }
.nav-link.active { color: #800080; }

.socials {
  display: flex;
  gap: 1rem;
  margin-top: auto;
  margin-bottom: 1.5rem;
}

.social-icon {
  color: #555;
  transition: color 0.2s ease;
}

.social-icon:hover { color: #800080; }

.scroll-hint {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.4rem;
}

.scroll-text {
  writing-mode: vertical-rl;
  text-orientation: mixed;
  font-size: 0.6rem;
  letter-spacing: 0.15em;
  color: #444;
  text-transform: lowercase;
}

.scroll-arrow {
  color: #444;
  font-size: 0.75rem;
  animation: bounce 1.8s infinite ease-in-out;
}

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50%       { transform: translateY(5px); }
}
html {
  scroll-behavior: smooth;
}
</style>
