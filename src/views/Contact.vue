<template>
  <div class="contact-page">
    <div class="container">
      <!-- Page Header -->
      <div class="page-header text-center mb-5">
        <h1 class="page-title">
          <i class="bi bi-envelope-heart me-3"></i>
          Contact <span class="gradient-text">Us</span>
        </h1>
        <p class="page-subtitle">
          Get in touch with our team - we'd love to hear from you
        </p>
      </div>

      <!-- Contact Info Cards -->
      <div class="contact-info-section mb-5">
        <div class="row g-4">
          <div class="col-md-4">
            <div class="contact-info-card">
              <div class="info-icon">
                <i class="bi bi-geo-alt-fill"></i>
              </div>
              <h5 class="info-title">Our Location</h5>
              <p class="info-text">Suez, Egypt</p>
            </div>
          </div>
          <div class="col-md-4">
            <div class="contact-info-card">
              <div class="info-icon">
                <i class="bi bi-telephone-fill"></i>
              </div>
              <h5 class="info-title">Call Us</h5>
              <p class="info-text">
                <a href="tel:+201208867209">+20 120 886 7209</a>
              </p>
            </div>
          </div>
          <div class="col-md-4">
            <div class="contact-info-card">
              <div class="info-icon">
                <i class="bi bi-envelope-fill"></i>
              </div>
              <h5 class="info-title">Email Us</h5>
              <p class="info-text">
                <a href="mailto:omarmohammedabdelradi@gmail.com">
                  omarmohammedabdelradi@gmail.com
                </a>
              </p>
            </div>
          </div>
        </div>
      </div>

      <!-- Google Map -->
      <div class="map-section mb-5">
        <div class="map-container">
          <iframe
            class="map"
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d55297.32117951782!2d32.55269463872721!3d29.977056838849066!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x1456257838ae4111%3A0x1f0a056a97ea1bc0!2z2KfZhNiz2YjZitiz2Iwg2YXYrdin2YHYuNipINin2YTYs9mI2YrYsw!5e0!3m2!1sar!2seg!4v1756687694507!5m2!1sar!2seg"
            width="100%"
            height="400"
            style="border: 0"
            allowfullscreen=""
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
          ></iframe>
        </div>
      </div>

      <!-- Contact Form -->
      <div class="form-section">
        <div class="row">
          <div class="col-lg-8 mx-auto">
            <!-- Success Message -->
            <div v-if="success" class="success-message">
              <i class="bi bi-check-circle-fill me-2"></i>
              Thank you for contacting us! We'll get back to you soon.
            </div>

            <!-- Contact Form -->
            <div class="contact-form-card">
              <h3 class="form-title">Send us a Message</h3>
              <form @submit.prevent="submitForm" class="contact-form">
                <div class="form-group">
                  <label class="form-label">Full Name</label>
                  <input
                    v-model="form.name"
                    type="text"
                    class="form-input"
                    placeholder="Enter your full name"
                  />
                  <div v-if="errors.name" class="error-message">
                    {{ errors.name }}
                  </div>
                </div>

                <div class="form-group">
                  <label class="form-label">Email Address</label>
                  <input
                    v-model="form.email"
                    type="email"
                    class="form-input"
                    placeholder="Enter your email address"
                  />
                  <div v-if="errors.email" class="error-message">
                    {{ errors.email }}
                  </div>
                </div>

                <div class="form-group">
                  <label class="form-label">Message</label>
                  <textarea
                    v-model="form.message"
                    rows="5"
                    class="form-input form-textarea"
                    placeholder="Write your message here..."
                  ></textarea>
                  <div v-if="errors.message" class="error-message">
                    {{ errors.message }}
                  </div>
                </div>

                <button type="submit" class="btn btn-submit">
                  <i class="bi bi-send me-2"></i>
                  Send Message
                </button>
              </form>
            </div>
          </div>
        </div>
      </div>

      <!-- Social Media -->
      <div class="social-section">
        <h4 class="social-title">Follow Us</h4>
        <div class="social-links">
          <a href="https://www.facebook.com/omar.mohammed.665257" target="_blank" class="social-link">
            <i class="bi bi-facebook"></i>
          </a>
          <a href="https://www.linkedin.com/in/omar-mohamed-a24783337/" target="_blank" class="social-link">
            <i class="bi bi-linkedin"></i>
          </a>
          <a href="https://instagram.com" target="_blank" class="social-link">
            <i class="bi bi-instagram"></i>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue"
import emailjs from "emailjs-com"

const form = ref({ name: "", email: "", message: "" })
const errors = ref({})
const success = ref(false)

function submitForm() {
  errors.value = {}
  success.value = false

  if (!form.value.name) errors.value.name = "Name is required"
  if (!form.value.email) errors.value.email = "Email is required"
  if (!form.value.message) errors.value.message = "Message is required"

  if (Object.keys(errors.value).length === 0) {
    emailjs
      .send(
        "service_ytzsitu",   
        "template_jkjhd5s",  
        {
          from_name: form.value.name,
          from_email: form.value.email,
          message: form.value.message,
          time: new Date().toLocaleString(), 
        },
        "w_2nvy1GQYg8Pi3C-"    
      )
      .then(() => {
        success.value = true
        form.value = { name: "", email: "", message: "" }
      })
      .catch((err) => {
        console.error("Error:", err)
      })
  }
}
</script>

<style scoped>
.contact-page {
  min-height: 100vh;
  padding-top: 120px;
  padding-bottom: 2rem;
}

/* Page Header */
.page-header {
  margin-bottom: 3rem;
}

.page-title {
  font-size: 3rem;
  font-weight: 700;
  color: #1f2937;
  margin-bottom: 1rem;
}

.gradient-text {
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-light) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.page-subtitle {
  font-size: 1.2rem;
  color: #4b5563;
  margin-bottom: 0;
  font-weight: 500;
}

/* Contact Info Section */
.contact-info-section {
  margin-bottom: 4rem;
}

.contact-info-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 2rem;
  text-align: center;
  transition: all 0.3s ease;
  height: 100%;
}

.contact-info-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.info-icon {
  width: 70px;
  height: 70px;
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-light) 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  font-size: 1.8rem;
  color: rgb(0, 0, 0);
  box-shadow: 0 8px 25px rgba(99, 102, 241, 0.3);
}

.info-title {
  font-size: 1.2rem;
  font-weight: 600;
  color: #1f2937;
  margin-bottom: 1rem;
}

.info-text {
  color: #6b7280;
  margin-bottom: 0;
}

.info-text a {
  color: var(--color-primary);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.info-text a:hover {
  color: var(--color-primary-light);
  text-decoration: underline;
}

/* Map Section */
.map-section {
  margin-bottom: 4rem;
}

.map-container {
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.map {
  filter: grayscale(100%) invert(92%) contrast(90%);
  border-radius: 20px;
}

/* Form Section */
.form-section {
  margin-bottom: 4rem;
}

.contact-form-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 3rem;
  transition: all 0.3s ease;
}

.contact-form-card:hover {
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.form-title {
  font-size: 1.8rem;
  font-weight: 600;
  color: #1f2937;
  margin-bottom: 2rem;
  text-align: center;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-label {
  color: #1f2937;
  font-weight: 600;
  margin-bottom: 0.5rem;
  font-size: 1rem;
}

.form-input {
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 12px;
  color: #1f2937;
  padding: 1rem;
  font-size: 1rem;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.form-input:focus {
  outline: none;
  background: rgba(255, 255, 255, 0.15);
  border-color: var(--color-primary);
  box-shadow: 0 0 20px rgba(99, 102, 241, 0.3);
  color: #1f2937;
}

.form-input::placeholder {
  color: #9ca3af;
}

.form-textarea {
  resize: vertical;
  min-height: 120px;
}

.error-message {
  color: #ef4444;
  font-size: 0.9rem;
  margin-top: 0.5rem;
}

.btn-submit {
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-light) 100%);
  border: none;
  border-radius: 12px;
  color: rgb(0, 0, 0);
  font-weight: 600;
  padding: 1rem 2rem;
  font-size: 1.1rem;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
  align-self: center;
  min-width: 200px;
}

.btn-submit:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(99, 102, 241, 0.6);
}

/* Success Message */
.success-message {
  background: linear-gradient(135deg, #10b981 0%, #059669 100%);
  color: rgb(0, 0, 0);
  padding: 1rem 1.5rem;
  border-radius: 12px;
  margin-bottom: 2rem;
  text-align: center;
  font-weight: 500;
  box-shadow: 0 4px 15px rgba(16, 185, 129, 0.3);
  animation: fadeIn 0.6s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Social Section */
.social-section {
  text-align: center;
  padding: 3rem 0;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.social-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: #1f2937;
  margin-bottom: 2rem;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
}

.social-link {
  width: 60px;
  height: 60px;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #1f2937;
  font-size: 1.5rem;
  transition: all 0.3s ease;
  text-decoration: none;
  backdrop-filter: blur(10px);
}

.social-link:hover {
  background: var(--color-primary);
  border-color: var(--color-primary);
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(99, 102, 241, 0.4);
  color: #1f2937;
  text-decoration: none;
}

/* Responsive Design */
@media (max-width: 768px) {
  .page-title {
    font-size: 2rem;
  }
  
  .contact-form-card {
    padding: 2rem;
  }
  
  .contact-info-card {
    padding: 1.5rem;
  }
  
  .social-links {
    gap: 1rem;
  }
  
  .social-link {
    width: 50px;
    height: 50px;
    font-size: 1.2rem;
  }
}
</style>
