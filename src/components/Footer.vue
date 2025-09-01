<template>
  <footer class="modern-footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-brand">
          <div class="brand-info">
            <i class="bi bi-bag-check-fill brand-icon"></i>
            <h5 class="brand-name">Brand Store</h5>
          </div>
          <p class="brand-description">
            Your premium destination for exceptional products and unforgettable shopping experiences.
          </p>
        </div>
        
        <div class="footer-links">
          <div class="link-section">
            <h6 class="link-title">Quick Links</h6>
            <ul class="link-list">
              <li><router-link to="/">Home</router-link></li>
              <li><router-link to="/products">Products</router-link></li>
              <li><router-link to="/about">About</router-link></li>
              <li><router-link to="/contact">Contact</router-link></li>
            </ul>
          </div>
          
          <div class="link-section">
            <h6 class="link-title">Support</h6>
            <ul class="link-list">
              <li><a href="#">Help Center</a></li>
              <li><a href="#">Shipping Info</a></li>
              <li><a href="#">Returns</a></li>
              <li><a href="#">Size Guide</a></li>
            </ul>
          </div>
          
          <div class="link-section">
            <h6 class="link-title">Connect</h6>
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
      
      <div class="footer-bottom">
        <div class="footer-bottom-content">
          <p class="copyright">
            &copy; 2025 Brand Store. All rights reserved.
          </p>
          <p class="developer">
            Crafted with <i class="bi bi-heart-fill text-danger"></i> by Omar Mohamed
          </p>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.modern-footer {
  background: rgba(15, 23, 42, 0.95);
  backdrop-filter: blur(20px);
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  margin-top: auto;
  padding: 3rem 0 1rem;
}

.footer-content {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 3rem;
  margin-bottom: 2rem;
}

.footer-brand {
  max-width: 300px;
}

.brand-info {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

.brand-icon {
  font-size: 2rem;
  color: var(--color-primary);
  margin-right: 0.75rem;
  filter: drop-shadow(0 2px 4px rgba(99, 102, 241, 0.3));
}

.brand-name {
  font-size: 1.5rem;
  font-weight: 700;
  color: white;
  margin: 0;
  background: linear-gradient(135deg, #ffffff 0%, #e0e7ff 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.brand-description {
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.6;
  margin: 0;
  font-size: 0.95rem;
}

.footer-links {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.link-section {
  display: flex;
  flex-direction: column;
}

.link-title {
  color: white;
  font-weight: 600;
  margin-bottom: 1rem;
  font-size: 1rem;
}

.link-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.link-list li a {
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  font-size: 0.9rem;
  transition: all 0.3s ease;
  padding: 0.25rem 0;
}

.link-list li a:hover {
  color: var(--color-primary);
  transform: translateX(5px);
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  width: 40px;
  height: 40px;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgba(255, 255, 255, 0.7);
  font-size: 1.1rem;
  transition: all 0.3s ease;
  text-decoration: none;
  backdrop-filter: blur(10px);
}

.social-link:hover {
  background: var(--color-primary);
  border-color: var(--color-primary);
  color: white;
  transform: translateY(-3px);
  box-shadow: 0 8px 20px rgba(99, 102, 241, 0.4);
  text-decoration: none;
}

.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  padding-top: 1.5rem;
}

.footer-bottom-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.copyright {
  color: rgba(255, 255, 255, 0.6);
  margin: 0;
  font-size: 0.9rem;
}

.developer {
  color: rgba(255, 255, 255, 0.6);
  margin: 0;
  font-size: 0.9rem;
  display: flex;
  align-items: center;
  gap: 0.25rem;
}

/* Responsive Design */
@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .footer-links {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
  
  .footer-bottom-content {
    flex-direction: column;
    text-align: center;
    gap: 0.5rem;
  }
  
  .brand-info {
    justify-content: center;
  }
  
  .social-links {
    justify-content: center;
  }
}

@media (max-width: 576px) {
  .modern-footer {
    padding: 2rem 0 1rem;
  }
  
  .footer-content {
    gap: 1.5rem;
  }
  
  .brand-name {
    font-size: 1.3rem;
  }
  
  .brand-icon {
    font-size: 1.5rem;
  }
}
</style>