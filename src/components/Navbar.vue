<template>
  <nav class="navbar" :class="{ 'navbar-hidden': !showNavbar }">
    <div class="container navbar-content">
      <router-link to="/" class="logo">
        <img src="https://image2url.com/images/1764902453031-86c95471-3ad8-46c6-9f9b-3196954dcfec.png" alt="Poetnam Shop" class="logo-image" />
        <span class="logo-text">Poetnam Shop</span>
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
import { ref, onMounted, onUnmounted } from 'vue'
import { ShoppingCart, Menu, X } from 'lucide-vue-next'
import { useCartStore } from '@/stores'

const cartStore = useCartStore()
const menuOpen = ref(false)
const showNavbar = ref(true)
const lastScrollPosition = ref(0)

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}

const closeMenu = () => {
  menuOpen.value = false
}

const handleScroll = () => {
  const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop
  
  // Jika di posisi paling atas, selalu tampilkan navbar
  if (currentScrollPosition < 10) {
    showNavbar.value = true
    lastScrollPosition.value = currentScrollPosition
    return
  }
  
  // Jika scroll ke bawah, sembunyikan navbar
  if (currentScrollPosition > lastScrollPosition.value && currentScrollPosition > 100) {
    showNavbar.value = false
  } 
  // Jika scroll ke atas, tampilkan navbar
  else if (currentScrollPosition < lastScrollPosition.value) {
    showNavbar.value = true
  }
  
  lastScrollPosition.value = currentScrollPosition
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.navbar {
  background: white;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 50;
  transition: transform 0.3s ease-in-out, opacity 0.3s ease-in-out;
  transform: translateY(0);
  opacity: 1;
}

.navbar-hidden {
  transform: translateY(-100%);
  opacity: 0;
}

.navbar-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 5rem;
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  text-decoration: none;
  transition: transform 0.3s ease;
}

.logo:hover {
  transform: scale(1.05);
}

.logo-image {
  width: 50px;
  height: 50px;
  object-fit: contain;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.1));
}

.logo-text {
  font-size: 1.875rem;
  font-weight: 700;
  background: linear-gradient(to right, #ec4899, #9333ea);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
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
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(to right, #ec4899, #9333ea);
  transition: width 0.3s ease;
}

.nav-link:hover::after,
.nav-link.router-link-active::after {
  width: 100%;
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
  animation: bounce 0.5s ease;
}

@keyframes bounce {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.2); }
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
  transition: all 0.3s ease;
}

.mobile-link:hover,
.mobile-link.router-link-active {
  color: #ec4899;
  background: #fce7f3;
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