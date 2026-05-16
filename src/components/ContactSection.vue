<script setup>
import { ref } from "vue";

const form = ref({
  name: "",
  email: "",
  message: "",
});

const isSubmitting = ref(false);
const isSuccess = ref(false);

const submitForm = () => {
  isSubmitting.value = true;

  // Format the email
  const subject = encodeURIComponent(`Inquiry from ${form.value.name}`);
  const body = encodeURIComponent(
    `Name: ${form.value.name}\nEmail: ${form.value.email}\n\nMessage:\n${form.value.message}`
  );
  
  // Construct mailto link
  const mailtoLink = `mailto:fahrisetdarma@gmail.com?subject=${subject}&body=${body}`;
  
  // Open mail client
  window.location.href = mailtoLink;

  setTimeout(() => {
    isSubmitting.value = false;
    isSuccess.value = true;

    setTimeout(() => {
      isSuccess.value = false;
      form.value = { name: "", email: "", message: "" };
    }, 3000);
  }, 1000);
};
</script>

<template>
  <section id="contact" class="contact">
    <h2> What's Next?</h2>

    <div class="contact-container">
      <div class="contact-text">
        <h3 class="contact-title">Get In Touch</h3>
        <p>
          Although I'm not currently looking for any new opportunities, my inbox
          is always open. Whether you have a question or just want to say hi,
          I'll try my best to get back to you!
        </p>

        <div class="contact-info">
          <div class="info-item">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="var(--color-primary)"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <path
                d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"
              ></path>
              <polyline points="22,6 12,13 2,6"></polyline>
            </svg>
            <span>Fahrisetdarma@gmail.com</span>
          </div>
          <div class="info-item">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="var(--color-primary)"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
              <circle cx="12" cy="10" r="3"></circle>
            </svg>
            <span>Sidoarjo, Jawa Timur, ID</span>
          </div>
        </div>
      </div>

      <div class="contact-form-wrapper glass-panel">
        <form
          v-if="!isSuccess"
          @submit.prevent="submitForm"
          class="contact-form"
        >
          <div class="form-group">
            <label for="name">Name</label>
            <input
              type="text"
              id="name"
              v-model="form.name"
              required
              placeholder="Fahri Setia Darma"
            />
          </div>

          <div class="form-group">
            <label for="email">Email</label>
            <input
              type="email"
              id="email"
              v-model="form.email"
              required
              placeholder="Fahrisetdarma@gmail.com"
            />
          </div>

          <div class="form-group">
            <label for="message">Message</label>
            <textarea
              id="message"
              v-model="form.message"
              required
              rows="5"
              placeholder="Hello, I'd like to talk about..."
            ></textarea>
          </div>

          <button
            type="submit"
            class="btn-primary form-btn"
            :disabled="isSubmitting"
          >
            <span v-if="isSubmitting">Sending...</span>
            <span v-else>Send Message</span>
          </button>
        </form>

        <div v-else class="success-message">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="64"
            height="64"
            viewBox="0 0 24 24"
            fill="none"
            stroke="var(--color-success, #27c93f)"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <polyline points="20 6 9 17 4 12"></polyline>
          </svg>
          <h3>Message Sent!</h3>
          <p>Thanks for reaching out. I'll get back to you soon.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped src="../assets/css/ContactSection.css"></style>
