<script setup>
import { ref } from 'vue'
import projectImg1 from '../assets/project1.png'
import projectImg2 from '../assets/project2.png'
import preview from '../assets/preview.png'

const projects = ref([
  {
    id: 1,
    title: 'Business Performance Dashboard',
    subtitle: 'Strategic Data Visualization',
    description: 'Developed executive dashboards in Power BI providing real-time insights into key performance indicators. Focused on delivering actionable data for stakeholders through intuitive design and robust data modeling.',
    image: projectImg1,
    tags: ['Power BI', 'Postgresql', 'Excel'],
    github: '#',
    live: '#'
  },
  {
    id: 2,
    title: 'Enterprise Data Automation',
    subtitle: 'Efficiency & Accuracy',
    description: 'Engineered an automated data management system using Excel Macros and Power Query. Standardized record management and eliminated manual entry errors across multiple departments.',
    image: projectImg2,
    tags: ['VBA', 'Power Query', 'Automation'],
    github: '#',
    live: '#'
  },
  {
    id: 3,
    title: 'Dashboard & Reporting',
    subtitle: 'Web Dashboard',
    description: 'Web based data visualization platform built to explore and analyze the Superstore dataset, featuring interactive charts across profit, sales, category, and shipping dimensions.',
    image: preview, 
    tags: ['HTML', 'Javascript', 'CSS'],
    github: '#',
    live: '#'
  }
])
</script>

<template>
  <section id="projects" class="projects">
    <h2>Selected <span>Projects</span></h2>
    
    <div class="projects-list">
      <div v-for="project in projects" :key="project.id" class="project-item">
        <div class="project-visual">
          <img :src="project.image" :alt="project.title" />
          <!-- <div class="project-links">
            <a :href="project.github" target="_blank" class="hover-target">Source</a>
            <a :href="project.live" target="_blank" class="hover-target">Live View</a>
          </div> -->
        </div>
        
        <div class="project-info">
          <span class="project-subtitle">{{ project.subtitle }}</span>
          <h3 class="project-title">{{ project.title }}</h3>
          <p class="project-description">{{ project.description }}</p>
          <div class="project-tags">
            <span v-for="tag in project.tags" :key="tag">{{ tag }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped src="../assets/css/ProjectsSection.css"></style>
