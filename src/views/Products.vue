<template>
  <div class="products-page">
    <div class="container">
      <!-- Page Header -->
      <div class="page-header text-center mb-5">
        <h1 class="page-title">
           <span class="gradient-text  text-bg-dark">Our Products</span>
        </h1>
        <p class="page-subtitle">
          Discover our amazing collection of premium products
        </p>
      </div>

      <!-- Search + Sort + Category -->
      <div class="filters-section mb-5">
        <div class="row align-items-center g-3">
          <!-- Search -->
          <div class="col-md-4">
            <div class="search-container">
              <div class="search-input">
                <i class="bi bi-search search-icon"></i>
                <input 
                  v-model="search" 
                  type="text" 
                  class="form-control" 
                  placeholder="Search products..." />
              </div>
            </div>
          </div>

          <!-- Sort -->
          <div class="col-md-4">
            <div class="select-container">
              <select v-model="sortOption" class="form-select modern-select">
                <option value="">Sort by</option>
                <option value="asc">Price: Low → High</option>
                <option value="desc">Price: High → Low</option>
              </select>
            </div>
          </div>

          <!-- Category -->
          <div class="col-md-4">
            <div class="select-container">
              <select v-model="selectedCategory" class="form-select modern-select">
                <option value="">All Categories</option>
                <option v-for="cat in categories" :key="cat" :value="cat">{{ cat }}</option>
              </select>
            </div>
          </div>
        </div>
      </div>

      <!-- Alert -->
      <div 
        v-if="alertMessage" 
        class="alert alert-success alert-dismissible fade show modern-alert" 
        role="alert">
        <i class="bi bi-check-circle me-2"></i>
        {{ alertMessage }}
        <button 
          type="button" 
          class="btn-close" 
          @click="alertMessage = ''">
        </button>
      </div>

      <!-- Products grid -->
      <div class="products-grid">
        <div class="row g-4">
          <div 
            v-for="product in finalProducts" 
            :key="product.id" 
            class="col-md-4 col-lg-3">
            <div class="product-card">
              <div class="product-image">
                <img 
                  :src="product.image" 
                  :alt="product.title"
                  class="img-fluid" />
                <div class="product-overlay">
                  <button 
                    class="btn btn-primary add-to-cart-btn" 
                    @click="addToCart(product)">
                    <i class="bi bi-cart-plus me-2"></i> Add to Cart
                  </button>
                </div>
              </div>
              <div class="product-info">
                <h5 class="product-title">{{ product.title }}</h5>
                <div class="product-price">
                  <span class="price">${{ product.price }}</span>
                  <span class="category">{{ product.category }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import cartStore from '../cartStore'   // ✅ استدعاء الـ store

const products = ref([])
const search = ref('')
const sortOption = ref('')
const selectedCategory = ref('')
const alertMessage = ref('')
const categories = ref([])

const { addToCart } = cartStore   // ✅ خد الفنكشن من الـ store

// فلترة المنتجات
const filteredProducts = computed(() =>
  products.value.filter(p =>
    p.title.toLowerCase().includes(search.value.toLowerCase()) &&
    (selectedCategory.value ? p.category === selectedCategory.value : true)
  )
)

// ترتيب
const finalProducts = computed(() => {
  let sorted = [...filteredProducts.value]
  if (sortOption.value === 'asc') {
    sorted.sort((a, b) => a.price - b.price)
  } else if (sortOption.value === 'desc') {
    sorted.sort((a, b) => b.price - a.price)
  }
  return sorted
})

// تحميل المنتجات
onMounted(async () => {
  const res = await fetch('https://fakestoreapi.com/products')
  products.value = await res.json()
  categories.value = [...new Set(products.value.map(p => p.category))]
})

// ✅ دالة إضافة للكارت
function handleAdd(product) {
  addToCart(product)
  alertMessage.value = `${product.title} added to cart ✅`
}
</script>

<style scoped>
.products-page {
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
  color: #030303;
  margin-bottom: 0;
  font-weight: 500;
}

/* Filters Section */
.filters-section {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 2rem;
  margin-bottom: 3rem;
}

.search-container {
  position: relative;
}

.search-input {
  position: relative;
}

.search-icon {
  position: absolute;
  left: 1rem;
  top: 50%;
  transform: translateY(-50%);
  color: var(--color-primary);
  font-size: 1.2rem;
  z-index: 2;
}

.search-input .form-control {
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgb(0, 0, 0);
  border-radius: 12px;
  color: rgb(2, 2, 2);
  padding: 1rem 1rem 1rem 3rem;
  font-size: 1rem;
  transition: all 0.3s ease;
}

.search-input .form-control:focus {
  background: rgba(255, 255, 255, 0.15);
  border-color: var(--color-primary);
  box-shadow: 0 0 20px rgba(99, 102, 241, 0.3);
  color: rgb(0, 0, 0);
}

.search-input .form-control::placeholder {
  color: rgba(255, 255, 255, 0.6);
}

.select-container {
  position: relative;
}

.modern-select {
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgb(18, 18, 18);
  border-radius: 12px;
  color: rgb(0, 0, 0);
  padding: 1rem;
  font-size: 1rem;
  transition: all 0.3s ease;
}

.modern-select:focus {
  background: rgba(255, 255, 255, 0.15);
  border-color: var(--color-primary);
  box-shadow: 0 0 20px rgba(99, 102, 241, 0.3);
  color: rgb(0, 0, 0);
}

.modern-select option {
  background: #f1f1f2;
  color: rgb(0, 0, 0);
}

/* Alert */
.modern-alert {
  background: linear-gradient(135deg, #10b981 0%, #059669 100%);
  border: none;
  border-radius: 12px;
  color: rgb(0, 0, 0);
  border-left: 4px solid #34d399;
  box-shadow: 0 4px 15px rgba(16, 185, 129, 0.3);
}

/* Products Grid */
.products-grid {
  margin-top: 2rem;
}

.product-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  overflow: hidden;
  transition: all 0.3s ease;
  height: 100%;
  position: relative;
}

.product-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.product-image {
  position: relative;
  height: 250px;
  overflow: hidden;
}

.product-image img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  padding: 1rem;
  transition: transform 0.3s ease;
}

.product-card:hover .product-image img {
  transform: scale(1.05);
}

.product-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.product-card:hover .product-overlay {
  opacity: 1;
}

.add-to-cart-btn {
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-light) 100%);
  border: none;
  border-radius: 12px;
  color: rgb(255, 255, 255);
  padding: 0.75rem 1.5rem;
  font-weight: 600;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
}

.add-to-cart-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(99, 102, 241, 0.6);
  color: rgb(0, 0, 0);
}

.product-info {
  padding: 1.5rem;
}

.product-title {
  font-size: 1.1rem;
  font-weight: 600;
  color: #1f2937;
  margin-bottom: 1rem;
  line-height: 1.4;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.product-price {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.price {
  font-size: 1.3rem;
  font-weight: 700;
  color: var(--color-accent);
  text-shadow: 0 2px 4px rgba(245, 158, 11, 0.3);
}

.category {
  font-size: 0.85rem;
  color: #6b7280;
  background: rgba(255, 255, 255, 0.1);
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  text-transform: capitalize;
}

/* Responsive Design */
@media (max-width: 768px) {
  .page-title {
    font-size: 2rem;
  }
  
  .filters-section {
    padding: 1.5rem;
  }
  
  .product-image {
    height: 200px;
  }
  
  .product-info {
    padding: 1rem;
  }
}
</style>
