<script setup>
import { onMounted, ref } from 'vue'

const displayedTitle = ref('')
const titles = ['IT Developer']
let titleIndex = 0
let charIndex = 0
let isDeleting = false

const type = () => {
  const currentTitle = titles[titleIndex]
  
  if (isDeleting) {
    displayedTitle.value = currentTitle.substring(0, charIndex - 1)
    charIndex--
  } else {
    displayedTitle.value = currentTitle.substring(0, charIndex + 1)
    charIndex++
  }

  let typeSpeed = isDeleting ? 50 : 100

  if (!isDeleting && charIndex === currentTitle.length) {
    typeSpeed = 2000
    isDeleting = true
  } else if (isDeleting && charIndex === 0) {
    isDeleting = false
    titleIndex = (titleIndex + 1) % titles.length
    typeSpeed = 500
  }

  setTimeout(type, typeSpeed)
}

// const stats = ref([
//   { label: 'Projects Completed', value: 0, target: 12, suffix: '+' },
//   { label: 'Years Experience', value: 0, target: 1, suffix: '+' },
//   { label: 'Happy Clients', value: 0, target: 5, suffix: '' },
// ])

const animateStats = () => {
  stats.value.forEach(stat => {
    const duration = 2000
    const start = 0
    const end = stat.target
    const stepTime = Math.abs(Math.floor(duration / end))
    
    let current = start
    const timer = setInterval(() => {
      current++
      stat.value = current
      if (current === end) {
        clearInterval(timer)
      }
    }, stepTime)
  })
}

onMounted(() => {
  type()
  setTimeout(animateStats, 1000)
})
</script>

<template>
  <section id="home" class="hero">
    <div class="hero-container">
      <div class="hero-main">
        <div class="hero-text">
          <!-- <p class="hero-overline fade-in">Available for new opportunities</p> -->
          <h1 class="hero-title fade-in" style="animation-delay: 0.2s">
            Building digital <br />
            <span>experiences</span> with <br />
            precision<span>.</span>
          </h1>
          <div class="hero-typewriter fade-in" style="animation-delay: 0.4s">
            I am a <span class="typing">{{ displayedTitle }}</span><span class="cursor">|</span>
          </div>
          <p class="hero-description fade-in" style="animation-delay: 0.6s">
            Fresh Informatics graduate passionate about software development. 
            Specializing in building robust applications with ASP.NET Core, C#, and modern frontend frameworks like Vue.js and Angular.
          </p>
          <div class="hero-actions fade-in" style="animation-delay: 0.8s">
            <a href="#projects" class="btn-primary hover-target">Explore Portfolio</a>
            <a href="#contact" class="btn-outline hover-target">Get in Touch</a>
          </div>
        </div>
        
        <div class="hero-visual fade-in" style="animation-delay: 1s">
          <div class="visual-container">
            <div class="decorative-letter">F</div>
            <div class="image-reveal">
              <img src="../assets/profile.jpg" alt="Fahri Setia Darma" />
              <div class="image-overlay-texture"></div>
            </div>
            <div class="floating-circle"></div>
            <div class="hero-stack-floating">
              <div class="stack-item"><span>Vue.js</span></div>
              <div class="stack-item"><span>Angular.js</span></div>
              <div class="stack-item"><span>ASP.NET</span></div>
              <div class="stack-item"><span>SQL</span></div>
            </div>
          </div>
        </div>
      </div>

      <div class="hero-stats fade-in" style="animation-delay: 1.2s">
        <div v-for="stat in stats" :key="stat.label" class="stat-item">
          <span class="stat-value">{{ stat.value }}{{ stat.suffix }}</span>
          <span class="stat-label">{{ stat.label }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped src="../assets/css/HeroSection.css"></style>
