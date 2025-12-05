<template>
  <nav class="navbar">
    <div class="container navbar-content">
      <router-link to="/" class="logo">
        Poetnam Shop
      </router-link>

      <!-- Desktop Menu -->
      <div class="desktop-menu">
        <router-link to="/" class="nav-link">Home</router-link>
        <router-link to="/products" class="nav-link">Produk</router-link>
        <router-link to="/about" class="nav-link">Tentang</router-link>
        <router-link to="/cart" class="cart-button">
          <ShoppingCart :size="24" />
          <span v-if="cartStore.cartItemsCount > 0" class="cart-badge">
            {{ cartStore.cartItemsCount }}
          </span>
        </router-link>
      </div>

      <!-- Mobile Menu Button -->
      <button class="mobile-menu-btn" @click="toggleMenu">
        <Menu v-if="!menuOpen" :size="28" />
        <X v-else :size="28" />
      </button>
    </div>

    <!-- Mobile Menu -->
    <transition name="slide">
      <div v-if="menuOpen" class="mobile-menu">
        <router-link to="/" class="mobile-link" @click="closeMenu">Home</router-link>
        <router-link to="/products" class="mobile-link" @click="closeMenu">Produk</router-link>
        <router-link to="/about" class="mobile-link" @click="closeMenu">Tentang</router-link>
        <router-link to="/cart" class="mobile-link" @click="closeMenu">
          Keranjang ({{ cartStore.cartItemsCount }})
        </router-link>
      </div>
    </transition>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
import { ShoppingCart, Menu, X } from 'lucide-vue-next'
import { useCartStore } from '@/stores'

const cartStore = useCartStore()
const menuOpen = ref(false)

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}

const closeMenu = () => {
  menuOpen.value = false
}
</script>

<style scoped>
.navbar {
  background: white;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 50;
}

.navbar-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 5rem;
}

.logo {
  font-size: 1.875rem;
  font-weight: 700;
  background: linear-gradient(to right, #ec4899, #9333ea);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-decoration: none;
}

.desktop-menu {
  display: none;
  align-items: center;
  gap: 2rem;
}

@media (min-width: 768px) {
  .desktop-menu {
    display: flex;
  }
}

.nav-link {
  font-size: 1.125rem;
  font-weight: 600;
  color: #4b5563;
  text-decoration: none;
  transition: color 0.3s ease;
}

.nav-link:hover,
.nav-link.router-link-active {
  color: #ec4899;
}

.cart-button {
  position: relative;
  background: linear-gradient(to right, #ec4899, #9333ea);
  color: white;
  padding: 0.75rem;
  border-radius: 9999px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  text-decoration: none;
}

.cart-button:hover {
  transform: scale(1.1);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

.cart-badge {
  position: absolute;
  top: -0.5rem;
  right: -0.5rem;
  background: #ef4444;
  color: white;
  width: 1.5rem;
  height: 1.5rem;
  border-radius: 9999px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.875rem;
  font-weight: 700;
}

.mobile-menu-btn {
  display: block;
  background: none;
  border: none;
  cursor: pointer;
  color: #1f2937;
}

@media (min-width: 768px) {
  .mobile-menu-btn {
    display: none;
  }
}

.mobile-menu {
  padding: 1rem 0;
  background: white;
  border-top: 1px solid #e5e7eb;
}

.mobile-link {
  display: block;
  padding: 0.75rem 1rem;
  font-size: 1.125rem;
  font-weight: 600;
  color: #4b5563;
  text-decoration: none;
  transition: color 0.3s ease;
}

.mobile-link:hover,
.mobile-link.router-link-active {
  color: #ec4899;
}

.slide-enter-active,
.slide-leave-active {
  transition: all 0.3s ease;
}

.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>