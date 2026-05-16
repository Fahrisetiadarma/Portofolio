<script setup>
import { ref } from 'vue'

const certifications = ref([
  {
    id: 1,
    title: 'AWS Certified Cloud Practitioner',
    issuer: 'Amazon Web Services',
    date: 'Jan 2024',
    credentialId: 'AWS-1234567',
    link: '#'
  },
  {
    id: 2,
    title: 'Frontend Developer (React)',
    issuer: 'HackerRank',
    date: 'Dec 2023',
    credentialId: 'HR-7654321',
    link: '#'
  },
  {
    id: 3,
    title: 'Data Analytics Professional',
    issuer: 'Google',
    date: 'Nov 2023',
    credentialId: 'GOOG-9876543',
    link: '#'
  }
])
</script>

<template>
  <section id="certifications" class="certifications">
    <h2><span>04.</span> Certifications</h2>
    
    <div class="certifications-grid">
      <div v-for="cert in certifications" :key="cert.id" class="cert-card glass-panel">
        <div class="cert-icon">
          <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="var(--color-primary)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <circle cx="12" cy="8" r="7"></circle>
            <polyline points="8.21 13.89 7 23 12 20 17 23 15.79 13.88"></polyline>
          </svg>
        </div>
        <div class="cert-content">
          <h3 class="cert-title">{{ cert.title }}</h3>
          <p class="cert-issuer">{{ cert.issuer }}</p>
          <div class="cert-details">
            <span class="cert-date">{{ cert.date }}</span>
            <span class="cert-id" v-if="cert.credentialId">ID: {{ cert.credentialId }}</span>
          </div>
        </div>
        <a :href="cert.link" target="_blank" rel="noopener noreferrer" class="cert-link" aria-label="View Credential">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
            <polyline points="15 3 21 3 21 9"></polyline>
            <line x1="10" y1="14" x2="21" y2="3"></line>
          </svg>
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped src="../assets/css/CertificationsSection.css"></style>
