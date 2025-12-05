<template>
  <div class="cart-page">
    <div class="container">
      <h1 class="page-title animate-slideInDown">Keranjang Belanja</h1>

      <!-- Empty Cart -->
      <div v-if="cartStore.items.length === 0" class="empty-cart animate-fadeIn">
        <ShoppingCart :size="80" class="empty-icon" />
        <p class="empty-text">Keranjang Anda masih kosong</p>
        <router-link to="/products" class="btn-primary">
          Mulai Belanja
        </router-link>
      </div>

      <!-- Cart Items -->
      <div v-else>
        <div class="cart-items">
          <Cart 
            v-for="(item, index) in cartStore.items" 
            :key="item.id"
            :item="item"
            :style="{ animationDelay: `${index * 100}ms` }"
          />
        </div>

        <!-- Cart Summary -->
        <div class="cart-summary animate-fadeIn">
          <div class="summary-row">
            <span class="summary-label">Total:</span>
            <span class="summary-value">
              Rp {{ cartStore.cartTotal.toLocaleString('id-ID') }}
            </span>
          </div>
          <button class="checkout-btn">
            Checkout
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ShoppingCart } from 'lucide-vue-next'
import Cart from '../components/Cart.vue'
import { useCartStore } from '@/stores'

const cartStore = useCartStore()
</script>

<style scoped>
.cart-page {
  min-height: 100vh;
  background: linear-gradient(135deg, #fce7f3 0%, #f3e8ff 100%);
  padding: 5rem 0;
  animation: fadeIn 0.6s ease-out;
}

.page-title {
  font-size: 3rem;
  font-weight: 700;
  color: #1f2937;
  margin-bottom: 3rem;
}

.empty-cart {
  background: white;
  border-radius: 1rem;
  padding: 4rem 3rem;
  text-align: center;
}

.empty-icon {
  color: #d1d5db;
  margin: 0 auto 1.5rem;
}

.empty-text {
  font-size: 1.5rem;
  color: #6b7280;
  margin-bottom: 1.5rem;
}

.cart-items {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 2rem;
}

.cart-summary {
  background: white;
  border-radius: 1rem;
  padding: 2rem;
}

.summary-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.summary-label {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1f2937;
}

.summary-value {
  font-size: 1.875rem;
  font-weight: 700;
  color: #ec4899;
}

.checkout-btn {
  width: 100%;
  background: linear-gradient(to right, #ec4899, #9333ea);
  color: white;
  padding: 1rem;
  border-radius: 0.5rem;
  font-size: 1.125rem;
  font-weight: 700;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
}

.checkout-btn:hover {
  transform: scale(1.05);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

@media (max-width: 768px) {
  .cart-page {
    padding: 3rem 0;
  }

  .page-title {
    font-size: 2rem;
  }

  .empty-cart {
    padding: 3rem 1.5rem;
  }
}
</style>