<template>
  <div class="cart-page">
    <div class="container">
      <!-- Page Header -->
      <div class="page-header text-center mb-5">
        <h1 class="page-title">
          <i class="bi bi-cart3 me-3"></i>
          Your <span class="gradient-text">Cart</span>
        </h1>
        <p class="page-subtitle">
          Review your selected items before checkout
        </p>
      </div>

      <!-- Empty Cart -->
      <div v-if="cart.items.length === 0" class="empty-cart">
        <div class="empty-cart-content">
          <i class="bi bi-cart-x empty-cart-icon"></i>
          <h3 class="empty-cart-title">Your cart is empty</h3>
          <p class="empty-cart-text">Looks like you haven't added any items to your cart yet.</p>
          <router-link to="/products" class="btn btn-primary btn-lg">
            <i class="bi bi-bag-plus me-2"></i>
            Start Shopping
          </router-link>
        </div>
      </div>

      <!-- Cart Items -->
      <div v-else class="cart-content">
        <div class="row g-4 mb-5">
          <div
            v-for="item in cart.items"
            :key="item.id"
            class="col-12 col-md-6 col-lg-4"
          >
            <div class="cart-item-card">
              <div class="cart-item-image">
                <img
                  :src="item.image"
                  :alt="item.title"
                  class="img-fluid" />
              </div>
              <div class="cart-item-info">
                <h5 class="cart-item-title">{{ item.title }}</h5>
                <p class="cart-item-price">${{ item.price }}</p>

                <div class="quantity-section">
                  <div class="quantity-controls">
                    <button class="quantity-btn" @click="decreaseQuantity(item.id)">
                      <i class="bi bi-dash"></i>
                    </button>
                    <span class="quantity-value">{{ item.quantity }}</span>
                    <button class="quantity-btn" @click="increaseQuantity(item.id)">
                      <i class="bi bi-plus"></i>
                    </button>
                  </div>
                  <div class="item-total">
                    <span class="total-label">Total:</span>
                    <span class="total-price">${{ (item.price * item.quantity).toFixed(2) }}</span>
                  </div>
                </div>

                <button
                  class="remove-btn"
                  @click="removeFromCart(item.id)"
                  title="Remove item"
                >
                  <i class="bi bi-trash3"></i>
                </button>
              </div>
            </div>
          </div>
        </div>

        <!-- Cart Summary -->
        <div class="cart-summary">
          <div class="summary-content">
            <div class="summary-info">
              <h4 class="summary-title">Order Summary</h4>
              <div class="summary-details">
                <div class="summary-row">
                  <span class="summary-label">Items ({{ cart.items.length }}):</span>
                  <span class="summary-value">${{ totalPrice.toFixed(2) }}</span>
                </div>
                <div class="summary-row">
                  <span class="summary-label">Shipping:</span>
                  <span class="summary-value free">FREE</span>
                </div>
                <div class="summary-row total-row">
                  <span class="summary-label">Total:</span>
                  <span class="summary-value total">${{ totalPrice.toFixed(2) }}</span>
                </div>
              </div>
            </div>
            <div class="checkout-section">
              <button class="btn btn-checkout">
                <i class="bi bi-credit-card me-2"></i>
                Proceed to Checkout
              </button>
              <router-link to="/products" class="btn btn-continue">
                <i class="bi bi-arrow-left me-2"></i>
                Continue Shopping
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import cartStore from '../cartStore'

// cart جاي من store
const { cart, removeFromCart, increaseQuantity, decreaseQuantity } = cartStore

// نحسب الإجمالي
const totalPrice = computed(() =>
  cart.items.reduce((sum, item) => sum + item.price * item.quantity, 0)
)
</script>

<style scoped>
.cart-page {
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
  color: #030404;
  margin-bottom: 0;
  font-weight: 500;
}

/* Empty Cart */
.empty-cart {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 400px;
}

.empty-cart-content {
  text-align: center;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(4, 3, 3, 0.2);
  border-radius: 20px;
  padding: 3rem 2rem;
  max-width: 400px;
}

.empty-cart-icon {
  font-size: 4rem;
  color: var(--color-primary);
  margin-bottom: 1.5rem;
}

.empty-cart-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: #1f2937;
  margin-bottom: 1rem;
}

.empty-cart-text {
  color: #060607;
  margin-bottom: 2rem;
  line-height: 1.6;
}

/* Cart Items */
.cart-item-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  overflow: hidden;
  transition: all 0.3s ease;
  height: 100%;
  position: relative;
}

.cart-item-card:hover {
  transform: translateY(-5px);
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
}

.cart-item-image {
  height: 200px;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(255, 255, 255, 0.05);
}

.cart-item-image img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  padding: 1rem;
}

.cart-item-info {
  padding: 1.5rem;
}

.cart-item-title {
  font-size: 1.1rem;
  font-weight: 600;
  color: #1f2937;
  margin-bottom: 0.5rem;
  line-height: 1.4;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.cart-item-price {
  font-size: 1.2rem;
  font-weight: 600;
  color: var(--color-accent);
  margin-bottom: 1rem;
}

.quantity-section {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.quantity-controls {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.quantity-btn {
  width: 35px;
  height: 35px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  background: rgba(255, 255, 255, 0.1);
  color: rgb(11, 11, 11);
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  font-size: 1rem;
}

.quantity-btn:hover {
  background: var(--color-primary);
  border-color: var(--color-primary);
  transform: scale(1.1);
}

.quantity-value {
  font-size: 1.1rem;
  font-weight: 600;
  color: #131315;
  min-width: 30px;
  text-align: center;
}

.item-total {
  text-align: right;
}

.total-label {
  font-size: 0.9rem;
  color: #0d0e0e;
  display: block;
}

.total-price {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--color-accent);
}

.remove-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  width: 35px;
  height: 35px;
  border: none;
  background: rgba(239, 68, 68, 0.2);
  color: #ef4444;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  font-size: 1rem;
}

.remove-btn:hover {
  background: #ef4444;
  color: rgb(6, 5, 5);
  transform: scale(1.1);
}

/* Cart Summary */
.cart-summary {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 2rem;
  margin-top: 2rem;
}

.summary-content {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 2rem;
  align-items: center;
}

.summary-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: #0a0b0b;
  margin-bottom: 1.5rem;
}

.summary-details {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.summary-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.summary-label {
  color: #000000;
  font-size: 1rem;
}

.summary-value {
  color: #000000;
  font-weight: 600;
  font-size: 1rem;
}

.summary-value.free {
  color: #10b981;
  font-weight: 700;
}

.summary-row.total-row {
  border-top: 1px solid rgba(255, 255, 255, 0.2);
  padding-top: 1rem;
  margin-top: 0.5rem;
}

.summary-value.total {
  font-size: 1.3rem;
  font-weight: 700;
  color: var(--color-accent);
}

.checkout-section {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  min-width: 200px;
}

.btn-checkout {
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-light) 100%);
  border: none;
  color: rgb(0, 0, 0);
  padding: 1rem 2rem;
  border-radius: 12px;
  font-weight: 600;
  font-size: 1.1rem;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
}

.btn-checkout:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(99, 102, 241, 0.6);
  color: rgb(0, 0, 0);
}

.btn-continue {
  background: transparent;
  border: 2px solid rgba(255, 255, 255, 0.3);
  color: rgb(0, 0, 0);
  padding: 0.75rem 1.5rem;
  border-radius: 12px;
  font-weight: 500;
  transition: all 0.3s ease;
  text-decoration: none;
  text-align: center;
}

.btn-continue:hover {
  background: rgba(255, 255, 255, 0.1);
  border-color: rgba(255, 255, 255, 0.5);
  color: rgb(0, 0, 0);
  text-decoration: none;
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
  text-decoration: none;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(99, 102, 241, 0.6);
  color: rgb(0, 0, 0);
  text-decoration: none;
}

/* Responsive Design */
@media (max-width: 768px) {
  .page-title {
    font-size: 2rem;
  }
  
  .summary-content {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
  
  .checkout-section {
    min-width: auto;
  }
  
  .cart-item-info {
    padding: 1rem;
  }
  
  .quantity-section {
    flex-direction: column;
    gap: 1rem;
    align-items: stretch;
  }
  
  .item-total {
    text-align: center;
  }
}
</style>
