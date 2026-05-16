<script setup>
import { ref } from "vue";

const experiences = ref([
  {
    id: 1,
    company: "PT Mitra Pinasthika Mustika",
    role: "IT Developer",
    period: "Mar 2026 - Present",
    description: [
      "Developed and maintained SDMS (Salesman Dealer Management System), a web based platform supporting dealer sales operations and salesman management across multiple regions",
      "Implemented backend API services using ASP.NET MVC (C#) for handling suspect assignment, repeat order identification, and salesman allocation workflows",
      "Built and managed Windows Service job schedulers for automated data synchronization, including retry mechanisms for failed LMS/CRM API transmissions",
      "Integrated internal systems with external LMS and CRM platforms via REST API, managing lead data flow from suspect assignment through follow up stages",
      "Optimized SQL queries and stored procedures in SQL Server to support complex business logic such as repeat order detection and stage based data delivery",
    ],
  },
  {
    id: 2,
    company: "PT Bina Lintas Usaha Ekonomi",
    role: "Software Engineer",
    period: "Sept 2024 - Jan 2025",
    description: [
      "Developed the Solar Repository, an IoT-based website for monitoring Solar Power Plant (PLTS) data across Indonesia",
      "Implemented modern web technologies including React.js, Tailwind CSS, and React Leaflet",
      "Transformed complex IoT data into an intuitive and user friendly monitoring dashboard",
      "Integrated renewable energy data with web technology to enhance system usability",
    ],
  },
  {
    id: 3,
    company: "Dinas Kesehatan Kab.Sumbawa",
    role: "Project Manager",
    period: "Feb 2024 - Jun 2024",
    description: [
      "Led the end-to-end development of a web based Employee Attendance System by applying SDLC methodologies",
      "Translated client needs into technical specifications and implemented QR Code based attendance",
      "Directed team collaboration and stakeholder communication for successful project delivery",
    ],
  },
]);
</script>

<template>
  <section id="experience" class="experience">
    <h2>Professional <span>Journey</span></h2>

    <div class="timeline">
      <div
        v-for="exp in experiences"
        :key="exp.id"
        class="timeline-item"
      >
        <div class="timeline-header">
          <span class="period">{{ exp.period }}</span>
          <h3 class="role">{{ exp.role }}</h3>
          <span class="company">{{ exp.company }}</span>
        </div>
        
        <div class="timeline-body">
          <ul class="duties-list">
            <li v-for="(desc, dIndex) in exp.description" :key="dIndex">
              {{ desc }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped src="../assets/css/ExperienceSection.css"></style>
