<template>
  <div class="home-container">
    <!-- Hero Section -->
    <div class="hero-section">
      <div class="hero-content">
        <div class="hero-text">
          <h1 class="hero-title">
            <span class="gradient-text">Welcome to</span><br>
            <span class="brand-name">Brand Store</span>
      </h1>
          <p class="hero-subtitle">
            Your premium destination for exceptional products and unforgettable shopping experiences
          </p>
          <p class="hero-description">
            Discover our curated collection of high-quality products at unbeatable prices.<br>
            From <span class="highlight">electronics</span> to <span class="highlight">fashion</span>, 
            we have everything you need.
          </p>
          <div class="hero-buttons">
            <router-link to="/products" class="btn btn-primary btn-lg">
        <i class="bi bi-stars me-2"></i>
              Explore Products
            </router-link>
            <router-link to="/about" class="btn btn-outline btn-lg">
              <i class="bi bi-info-circle me-2"></i>
              Learn More
      </router-link>
    </div>
        </div>
        <div class="hero-visual">
          <div class="floating-cards">
            <div class="floating-card card-1">
              <i class="bi bi-laptop"></i>
              <span>Electronics</span>
            </div>
            <div class="floating-card card-2">
              <i class="bi bi-bag-heart"></i>
              <span>Fashion</span>
            </div>
            <div class="floating-card card-3">
              <i class="bi bi-house-gear"></i>
              <span>Home</span>
            </div>
          </div>
        </div>
        </div>
      </div>

    <!-- Features Section -->
    <div class="features-section">
      <div class="container">
        <h2 class="section-title text-center mb-5">
          Why Choose <span class="gradient-text">Brand Store</span>?
        </h2>
        <div class="row g-4">
      <div class="col-md-4">
            <div class="feature-card">
              <div class="feature-icon">
                <i class="bi bi-truck"></i>
              </div>
              <h5 class="feature-title">Lightning Fast Delivery</h5>
              <p class="feature-description">
                Get your orders delivered in record time with our premium shipping service.
              </p>
            </div>
          </div>
          <div class="col-md-4">
            <div class="feature-card">
              <div class="feature-icon">
                <i class="bi bi-shield-check"></i>
              </div>
              <h5 class="feature-title">Secure & Safe</h5>
              <p class="feature-description">
                Shop with complete confidence using our bank-level security system.
          </p>
        </div>
      </div>
      <div class="col-md-4">
            <div class="feature-card">
              <div class="feature-icon">
            <i class="bi bi-headset"></i>
          </div>
          <h5 class="feature-title">24/7 Support</h5>
              <p class="feature-description">
                Our dedicated support team is always here to help you with any questions.
          </p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Trust Section -->
    <div class="trust-section">
      <div class="container text-center">
        <h3 class="trust-title">Trusted by 10,000+ Happy Customers</h3>
        <div class="rating-stars">
          <i class="bi bi-star-fill"></i>
          <i class="bi bi-star-fill"></i>
          <i class="bi bi-star-fill"></i>
          <i class="bi bi-star-fill"></i>
          <i class="bi bi-star-fill"></i>
        </div>
        <p class="rating-text">4.9/5 average rating</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.home-container {
  min-height: 100vh;
  position: relative;
  overflow: hidden;
}

/* Hero Section */
.hero-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  padding: 2rem 0;
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.hero-text {
  z-index: 2;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 1.5rem;
  color: #1f2937;
}

.gradient-text {
  color: #374151;
  font-weight: 600;
}

.brand-name {
  color: #1f2937;
  font-weight: 800;
}

.hero-subtitle {
  font-size: 1.3rem;
  color: #4b5563;
  margin-bottom: 1rem;
  font-weight: 500;
}

.hero-description {
  font-size: 1.1rem;
  color: #6b7280;
  margin-bottom: 2rem;
  line-height: 1.6;
}

.highlight {
  color: var(--color-accent);
  font-weight: 600;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.btn-primary {
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-light) 100%);
  border: none;
  color: rgb(0, 0, 0);
  padding: 1rem 2rem;
  border-radius: 12px;
  font-weight: 600;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
}

.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(99, 102, 241, 0.6);
  color: rgb(0, 0, 0);
}

.btn-outline {
  background: transparent;
  border: 2px solid rgba(255, 255, 255, 0.3);
  color: rgb(0, 0, 0);
  padding: 1rem 2rem;
  border-radius: 12px;
  font-weight: 600;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.btn-outline:hover {
  background: rgba(255, 255, 255, 0.1);
  border-color: rgba(255, 255, 255, 0.5);
  transform: translateY(-3px);
  color: rgb(0, 0, 0);
}

/* Hero Visual */
.hero-visual {
  position: relative;
  height: 400px;
}

.floating-cards {
  position: relative;
  width: 100%;
  height: 100%;
}

.floating-card {
  position: absolute;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 2rem;
  text-align: center;
  color: rgb(0, 0, 0);
  animation: float 6s ease-in-out infinite;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
}

.floating-card i {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: var(--color-primary);
}

.floating-card span {
  display: block;
  font-weight: 600;
  font-size: 1.1rem;
}

.card-1 {
  top: 20%;
  left: 10%;
  animation-delay: 0s;
}

.card-2 {
  top: 50%;
  right: 20%;
  animation-delay: 2s;
}

.card-3 {
  bottom: 20%;
  left: 30%;
  animation-delay: 4s;
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-20px); }
}

/* Features Section */
.features-section {
  padding: 5rem 0;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: #000000;
  margin-bottom: 3rem;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
}

.feature-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 2.5rem 2rem;
  text-align: center;
  transition: all 0.3s ease;
  height: 100%;
}

.feature-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.feature-card .feature-icon {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-light) 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  font-size: 2rem;
  color: rgb(0, 0, 0);
  box-shadow: 0 8px 25px rgba(99, 102, 241, 0.3);
}

.feature-title {
  font-size: 1.4rem;
  font-weight: 600;
  color: #000000;
  margin-bottom: 1rem;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.2);
}

.feature-description {
  color: #000000;
  line-height: 1.6;
  font-size: 1rem;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}

/* Trust Section */
.trust-section {
  padding: 4rem 0;
  text-align: center;
}

.trust-title {
  font-size: 2rem;
  font-weight: 600;
  color: #000000;
  margin-bottom: 2rem;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
}

.rating-stars {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.rating-stars i {
  font-size: 2rem;
  color: var(--color-accent);
  filter: drop-shadow(0 2px 4px rgba(245, 158, 11, 0.3));
}

.rating-text {
  color: #000000;
  font-size: 1.1rem;
  font-weight: 500;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.2);
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }
  
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-buttons {
    justify-content: center;
  }
  
  .floating-cards {
    height: 300px;
  }
  
  .floating-card {
    padding: 1.5rem;
  }
  
  .section-title {
    font-size: 2rem;
  }
}
</style>
