<template>
  <div class="about-page">
    <!-- Hero Section -->
    <section class="hero-section">
      <div class="hero-content">
        <div class="container">
          <div class="hero-text text-center">
            <h6 class="hero-badge">OUR STORY</h6>
            <h1 class="hero-title">
              About <span class="gradient-text">Brand Store</span>
            </h1>
            <p class="hero-description">
              Discover the passion, craftsmanship, and vision behind our premium product collections.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Our Story Content -->
    <div class="content-section">
      <div class="container">
        <div class="story-card">
          <h2 class="section-title">Our Story</h2>
          <p class="story-text">
            Brand Store was born from a bold vision: to redefine premium shopping by making it not only accessible, 
            but also inspiring and unforgettable. We believe that every product should tell a story, and every 
            customer should feel valued and appreciated.
          </p>
          <p class="story-text">
            Since our founding, we've been committed to curating the finest products from around the world, 
            ensuring that each item meets our high standards for quality, design, and value. Our passion for 
            excellence drives everything we do.
          </p>
        </div>
      </div>
    </div>

    <!-- Our Team -->
    <div class="team-section">
      <div class="container">
        <h2 class="section-title text-center">Our Amazing Team</h2>
        <div class="row g-4">
          <div class="col-md-4" v-for="(member, index) in team" :key="index">
            <div class="team-card">
              <div class="team-icon">
                <i :class="member.icon"></i>
              </div>
              <h5 class="team-name">{{ member.title }}</h5>
              <p class="team-role">{{ member.role }}</p>
              <p class="team-desc">{{ member.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Our Values -->
    <div class="values-section">
      <div class="container">
        <h2 class="section-title text-center">Our Core Values</h2>
        <div class="row g-4">
          <div class="col-md-4" v-for="(value, index) in values" :key="index">
            <div class="value-card">
              <div class="value-icon">
                <i :class="value.icon"></i>
              </div>
              <h5 class="value-title">{{ value.title }}</h5>
              <p class="value-desc">{{ value.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Additional Info -->
    <div class="info-section">
      <div class="container">
        <div class="row g-4">
          <div class="col-md-6" v-for="(extra, index) in extras" :key="index">
            <div class="info-card">
              <div class="info-icon">
                <i :class="extra.icon"></i>
              </div>
              <h5 class="info-title">{{ extra.title }}</h5>
              <p class="info-desc">{{ extra.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const team = [
  { icon: "bi bi-brush", title: "Creative Director", role: "Fashion & Design", desc: "Leads our creative vision..." },
  { icon: "bi bi-megaphone", title: "Brand Manager", role: "Brand Strategy & Marketing", desc: "Develops Brand Store's identity..." },
  { icon: "bi bi-star", title: "Style Curator", role: "Fashion & Trends", desc: "Curates collections and stays ahead of fashion trends..." }
]

const values = [
  { icon: "bi bi-award", title: "Premium Quality", desc: "We source only the finest materials..." },
  { icon: "bi bi-heart", title: "Customer Love", desc: "Every customer is part of the Brand Store family..." },
  { icon: "bi bi-clock-history", title: "Timeless Style", desc: "We create pieces that transcend trends..." }
]

const extras = [
  { icon: "bi bi-scissors", title: "Craftsmanship Excellence", desc: "Every piece is meticulously crafted..." },
  { icon: "bi bi-globe", title: "Global Inspiration", desc: "Our designs are inspired by fashion capitals worldwide..." }
]
</script>

<style scoped>
.about-page {
  min-height: 100vh;
}

/* Hero Section */
.hero-section {
  min-height: 60vh;
  display: flex;
  align-items: center;
  position: relative;
  background: linear-gradient(135deg, rgba(99, 102, 241, 0.8) 0%, rgba(139, 92, 246, 0.8) 100%),
              url('https://images.unsplash.com/photo-1441986300917-64674bd600d8?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80') center/cover;
  padding: 4rem 0;
}

.hero-content {
  position: relative;
  z-index: 2;
}

.hero-badge {
  display: inline-block;
  background: rgba(255, 255, 255, 0.2);
  color: rgb(255, 255, 255);
  padding: 0.5rem 1.5rem;
  border-radius: 25px;
  font-size: 0.9rem;
  font-weight: 600;
  letter-spacing: 1px;
  margin-bottom: 1.5rem;
  backdrop-filter: blur(10px);
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 800;
  color: #1f2937;
  margin-bottom: 1.5rem;
  line-height: 1.2;
}

.gradient-text {
  background: linear-gradient(135deg, #ffffff 0%, #e0e7ff 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-description {
  font-size: 1.3rem;
  color: #ffffff;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
  font-weight: 500;
}

/* Content Sections */
.content-section,
.team-section,
.values-section,
.info-section {
  padding: 5rem 0;
}

.content-section {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
}

.team-section {
  background: rgba(255, 255, 255, 0.02);
}

.values-section {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
}

.info-section {
  background: rgba(255, 255, 255, 0.02);
}

/* Section Titles */
.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: #1f2937;
  margin-bottom: 3rem;
  position: relative;
}

.section-title::after {
  content: '';
  width: 80px;
  height: 4px;
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-light) 100%);
  display: block;
  margin: 1rem auto 0;
  border-radius: 2px;
}

/* Story Card */
.story-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 3rem;
  text-align: center;
  max-width: 800px;
  margin: 0 auto;
}

.story-text {
  font-size: 1.1rem;
  color: #6b7280;
  line-height: 1.8;
  margin-bottom: 1.5rem;
}

/* Team Cards */
.team-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 2.5rem 2rem;
  text-align: center;
  transition: all 0.3s ease;
  height: 100%;
}

.team-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.team-icon {
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

.team-name {
  font-size: 1.3rem;
  font-weight: 600;
  color: #1f2937;
  margin-bottom: 0.5rem;
}

.team-role {
  color: var(--color-primary);
  font-weight: 500;
  margin-bottom: 1rem;
  font-size: 1rem;
}

.team-desc {
  color: #6b7280;
  line-height: 1.6;
  font-size: 0.95rem;
}

/* Value Cards */
.value-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 2.5rem 2rem;
  text-align: center;
  transition: all 0.3s ease;
  height: 100%;
}

.value-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.value-icon {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, var(--color-secondary) 0%, var(--color-accent) 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  font-size: 2rem;
  color: rgb(0, 0, 0);
  box-shadow: 0 8px 25px rgba(6, 182, 212, 0.3);
}

.value-title {
  font-size: 1.3rem;
  font-weight: 600;
  color: #1f2937;
  margin-bottom: 1rem;
}

.value-desc {
  color: #6b7280;
  line-height: 1.6;
  font-size: 0.95rem;
}

/* Info Cards */
.info-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 2.5rem 2rem;
  text-align: center;
  transition: all 0.3s ease;
  height: 100%;
}

.info-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.info-icon {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, var(--color-accent) 0%, #f97316 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  font-size: 2rem;
  color: rgb(0, 0, 0);
  box-shadow: 0 8px 25px rgba(245, 158, 11, 0.3);
}

.info-title {
  font-size: 1.3rem;
  font-weight: 600;
  color: #1f2937;
  margin-bottom: 1rem;
}

.info-desc {
  color: #6b7280;
  line-height: 1.6;
  font-size: 0.95rem;
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-description {
    font-size: 1.1rem;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .story-card {
    padding: 2rem;
  }
  
  .team-card,
  .value-card,
  .info-card {
    padding: 2rem 1.5rem;
  }
}
</style>
