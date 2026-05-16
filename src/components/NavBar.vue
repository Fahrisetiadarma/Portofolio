<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps(['currentTheme'])
const emit = defineEmits(['toggleTheme'])

const isScrolled = ref(false)
const isMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

const navLinks = [
  { name: 'Home', href: '#home' },
  { name: 'About', href: '#about' },
  { name: 'Experience', href: '#experience' },
  { name: 'Projects', href: '#projects' },
  // { name: 'Certifications', href: '#certifications' },
  { name: 'Contact', href: '#contact' },
]
</script>

<template>
  <nav :class="['navbar', { 'scrolled': isScrolled }]">
    <div class="nav-container">
      <!-- <a href="#home" class="logo">
        Fahri<span>.</span>
      </a> -->
      
      <div class="nav-right">
        <!-- Desktop Menu -->
        <ul class="nav-links">
          <li v-for="link in navLinks" :key="link.name">
            <a :href="link.href">{{ link.name }}</a>
          </li>
        </ul>

        <!-- Theme Toggle -->
        <button class="theme-toggle" @click="$emit('toggleTheme')" :aria-label="'Switch to ' + (currentTheme === 'dark' ? 'light' : 'dark') + ' mode'">
          <svg v-if="currentTheme === 'dark'" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="5"/><line x1="12" y1="1" x2="12" y2="3"/><line x1="12" y1="21" x2="12" y2="23"/><line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/><line x1="1" y1="12" x2="3" y2="12"/><line x1="21" y1="12" x2="23" y2="12"/><line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/><line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/></svg>
          <svg v-else xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
        </button>

        <!-- Mobile Menu Button -->
        <button class="mobile-toggle" @click="toggleMenu" aria-label="Toggle Menu">
          <svg v-if="!isMenuOpen" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <line x1="3" y1="12" x2="21" y2="12"></line>
            <line x1="3" y1="6" x2="21" y2="6"></line>
            <line x1="3" y1="18" x2="21" y2="18"></line>
          </svg>
          <svg v-else xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <line x1="18" y1="6" x2="6" y2="18"></line>
            <line x1="6" y1="6" x2="18" y2="18"></line>
          </svg>
        </button>
      </div>
    </div>

    <!-- Mobile Menu dropdown -->
    <div :class="['mobile-menu', { 'open': isMenuOpen }]">
      <ul>
        <li v-for="link in navLinks" :key="link.name">
          <a :href="link.href" @click="isMenuOpen = false">{{ link.name }}</a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped src="../assets/css/NavBar.css"></style>
