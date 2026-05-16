<script setup>
import { onMounted, ref } from 'vue'
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import CertificationsSection from './components/CertificationsSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'

const cursorX = ref(0)
const cursorY = ref(0)
const isHovering = ref(false)
const theme = ref(localStorage.getItem('theme') || 'dark')

const updateCursor = (e) => {
  cursorX.value = e.clientX
  cursorY.value = e.clientY
}

const toggleTheme = () => {
  theme.value = theme.value === 'dark' ? 'light' : 'dark'
  document.documentElement.setAttribute('data-theme', theme.value)
  localStorage.setItem('theme', theme.value)
}

onMounted(() => {
  document.documentElement.setAttribute('data-theme', theme.value)
  window.addEventListener('mousemove', updateCursor)
  
  // Section reveal observer
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('reveal')
      }
    })
  }, { threshold: 0.1 })

  document.querySelectorAll('section').forEach(section => {
    observer.observe(section)
  })

  // Handle hover states for cursor
  const handleHover = () => isHovering.value = true
  const handleUnhover = () => isHovering.value = false

  document.querySelectorAll('a, button, .hover-target').forEach(el => {
    el.addEventListener('mouseenter', handleHover)
    el.addEventListener('mouseleave', handleUnhover)
  })
})
</script>

<template>
  <div class="app-container">
    <div 
      class="cursor-follower" 
      :class="{ 'hovering': isHovering }"
      :style="{ left: cursorX + 'px', top: cursorY + 'px' }"
    ></div>
    
    <NavBar :current-theme="theme" @toggle-theme="toggleTheme" />
    <main>
      <HeroSection />
      <AboutSection />
      <ExperienceSection />
      <ProjectsSection />
      <!-- <CertificationsSection /> -->
      <ContactSection />
    </main>
    <Footer />
  </div>
</template>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex-grow: 1;
}
</style>
