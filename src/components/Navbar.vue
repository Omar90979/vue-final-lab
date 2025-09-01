<template>
  <nav class="navbar navbar-expand-lg fixed-top modern-navbar">
    <div class="container">
      <!-- Brand name -->
      <router-link class="navbar-brand d-flex align-items-center" to="/">
        <i class="bi bi-bag-check-fill me-2 brand-icon"></i>
        <span class="fw-bold brand-text">Brand Store</span>
      </router-link>

      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarNav">
        <!-- Left side -->
        <ul class="navbar-nav me-auto">
          <li class="nav-item">
            <router-link class="nav-link modern-nav-link" to="/">
              <i class="bi bi-house-door-fill me-1"></i> Home
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link modern-nav-link" to="/products">
              <i class="bi bi-box-seam me-1"></i> Products
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link modern-nav-link" to="/about">
              <i class="bi bi-info-circle-fill me-1"></i> About
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link modern-nav-link" to="/contact">
              <i class="bi bi-envelope-fill me-1"></i> Contact
            </router-link>
          </li>
        </ul>

        <!-- Right side: Cart -->
        <ul class="navbar-nav ms-auto">
          <li class="nav-item position-relative">
            <router-link class="nav-link cart-link" to="/cart">
              <i class="bi bi-cart-fill me-1"></i> Cart
              <span
                v-if="cartCount > 0"
                key="cart-badge"
                class="position-absolute top-0 start-100 translate-middle badge rounded-pill cart-badge pulse-badge"
                style="font-size: 0.7rem;"
              >
                {{ cartCount }}
              </span>
            </router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { computed } from 'vue'
import cartStore from '../cartStore'

const { cart } = cartStore

const cartCount = computed(() =>
  cart.items.reduce((sum, item) => sum + item.quantity, 0)
)
</script>

<style scoped>
/* Modern Navbar Styles */
.modern-navbar {
  background: rgba(255, 255, 255, 0.1) !important;
  backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
  padding: 1rem 0;
}

.modern-navbar:hover {
  background: rgba(255, 255, 255, 0.15) !important;
}

.brand-icon {
  color: var(--color-primary);
  font-size: 1.5rem;
  filter: drop-shadow(0 2px 4px rgba(99, 102, 241, 0.3));
}

.brand-text {
  color: #1f2937;
  font-size: 1.4rem;
  font-weight: 700;
}

.modern-nav-link {
  color: #374151 !important;
  font-weight: 600;
  padding: 0.5rem 1rem !important;
  border-radius: 8px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.modern-nav-link::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
  transition: left 0.5s;
}

.modern-nav-link:hover::before {
  left: 100%;
}

.modern-nav-link:hover {
  color: #1f2937 !important;
  background: rgba(99, 102, 241, 0.1);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(99, 102, 241, 0.2);
}

.cart-link {
  color: #1f2937 !important;
  font-weight: 600;
  padding: 0.5rem 1rem !important;
  border-radius: 8px;
  transition: all 0.3s ease;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
}

.cart-link:hover {
  color: #1f2937 !important;
  background: rgba(99, 102, 241, 0.2);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(99, 102, 241, 0.3);
}

.cart-badge {
  background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%) !important;
  color: #1f2937 !important;
  border: 2px solid #1f2937;
  box-shadow: 0 2px 8px rgba(245, 158, 11, 0.4);
  font-weight: 700;
}

/* Pulse animation for badge */
@keyframes pulse {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  50% {
    transform: scale(1.3);
    opacity: 0.8;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

.pulse-badge {
  animation: pulse 0.5s ease;
}

/* Navbar toggler */
.navbar-toggler {
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 8px;
}

.navbar-toggler:focus {
  box-shadow: 0 0 0 0.2rem rgba(99, 102, 241, 0.25);
}

.navbar-toggler-icon {
  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 30 30'%3e%3cpath stroke='rgba%2831, 41, 55, 0.8%29' stroke-linecap='round' stroke-miterlimit='10' stroke-width='2' d='M4 7h22M4 15h22M4 23h22'/%3e%3c/svg%3e");
}
</style>
