<template>
  <div class="home">
    <Hero />

    <!-- Features Section -->
    <section class="features-section">
      <div class="container">
        <h2 class="section-title animate-fadeIn">Mengapa Memilih Kami?</h2>
        <div class="features-grid">
          <div 
            v-for="(feature, index) in features" 
            :key="index"
            class="feature-card animate-fadeInUp"
            :style="{ animationDelay: `${index * 100}ms` }"
          >
            <div class="feature-icon">{{ feature.icon }}</div>
            <h3 class="feature-title">{{ feature.title }}</h3>
            <p class="feature-description">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Featured Products Section -->
    <section class="products-section">
      <div class="container">
        <h2 class="section-title">Produk Pilihan</h2>
        <ProductList :products="featuredProducts" />
        <div class="view-all-container">
          <router-link to="/products" class="btn-primary">
            Lihat Semua Produk
          </router-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import Hero from '../components/Hero.vue'
import ProductList from '../components/ProductList.vue'

const features = [
  {
    icon: '✨',
    title: 'Kualitas Premium',
    description: 'Bahan berkualitas tinggi dan jahitan rapi'
  },
  {
    icon: '💰',
    title: 'Harga Terjangkau',
    description: 'Harga bersahabat dengan kualitas terbaik'
  },
  {
    icon: '🚚',
    title: 'Pengiriman Cepat',
    description: 'Proses pengiriman yang cepat dan aman'
  }
]

const featuredProducts = [
  {
    id: 1,
    name: 'Gamis Syari Premium',
    price: 350000,
    category: 'gamis',
    image: 'https://images.unsplash.com/photo-1601513445506-2ab0d4fb4229?w=500&h=600&fit=crop'
  },
  {
    id: 2,
    name: 'Gamis Polos Elegant',
    price: 280000,
    category: 'gamis',
    image: 'https://images.unsplash.com/photo-1583391265740-d8e8c80f6c64?w=500&h=600&fit=crop'
  },
  {
    id: 3,
    name: 'Gamis Motif Bunga',
    price: 320000,
    category: 'gamis',
    image: 'https://images.unsplash.com/photo-1609505848912-b7c3b8b4beda?w=500&h=600&fit=crop'
  }
]
</script>

<style scoped>
.home {
  animation: fadeIn 0.6s ease-out;
}

.features-section {
  padding: 5rem 0;
  background: white;
}

.products-section {
  padding: 5rem 0;
  background: linear-gradient(135deg, #fce7f3 0%, #f3e8ff 100%);
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  text-align: center;
  color: #1f2937;
  margin-bottom: 4rem;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.feature-card {
  text-align: center;
  padding: 2rem;
  border-radius: 1rem;
  background: linear-gradient(135deg, #fce7f3 0%, #f3e8ff 100%);
  transition: all 0.3s ease;
}

.feature-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
}

.feature-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.feature-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1f2937;
  margin-bottom: 0.75rem;
}

.feature-description {
  color: #4b5563;
  line-height: 1.75;
}

.view-all-container {
  margin-top: 3rem;
  text-align: center;
}

@media (max-width: 768px) {
  .section-title {
    font-size: 2rem;
  }

  .features-section,
  .products-section {
    padding: 3rem 0;
  }
}
</style>