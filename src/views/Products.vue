<template>
  <div class="products-page">
    <div class="container">
      <h1 class="page-title animate-slideInDown">Semua Produk</h1>
      <ProductList :products="allProducts" />
    </div>
  </div>
</template>

<script setup>
import ProductList from '../components/ProductList.vue'

const allProducts = [
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
  },
  {
    id: 4,
    name: 'Kerudung Segi Empat',
    price: 75000,
    category: 'kerudung',
    image: 'https://images.unsplash.com/photo-1590736969955-71cc94901144?w=500&h=600&fit=crop'
  },
  {
    id: 5,
    name: 'Jilbab Pashmina',
    price: 85000,
    category: 'kerudung',
    image: 'https://images.unsplash.com/photo-1591369822096-ffd140ec948f?w=500&h=600&fit=crop'
  },
  {
    id: 6,
    name: 'Kerudung Instan',
    price: 65000,
    category: 'kerudung',
    image: 'https://images.unsplash.com/photo-1583391733981-5e611fc30018?w=500&h=600&fit=crop'
  },
  {
    id: 7,
    name: 'Gamis Brokat Mewah',
    price: 450000,
    category: 'gamis',
    image: 'https://images.unsplash.com/photo-1617019114583-affb34d1b3cd?w=500&h=600&fit=crop'
  },
  {
    id: 8,
    name: 'Gamis Casual Harian',
    price: 250000,
    category: 'gamis',
    image: 'https://images.unsplash.com/photo-1595777457583-95e059d581b8?w=500&h=600&fit=crop'
  },
  {
    id: 9,
    name: 'Kerudung Paris Premium',
    price: 95000,
    category: 'kerudung',
    image: 'https://images.unsplash.com/photo-1610652492500-698ff5c89e23?w=500&h=600&fit=crop'
  }
]
</script>

<style scoped>
.products-page {
  min-height: 100vh;
  background: linear-gradient(135deg, #fce7f3 0%, #f3e8ff 100%);
  padding: 5rem 0;
  animation: fadeIn 0.6s ease-out;
}

.page-title {
  font-size: 3rem;
  font-weight: 700;
  text-align: center;
  color: #1f2937;
  margin-bottom: 4rem;
}

@media (max-width: 768px) {
  .products-page {
    padding: 3rem 0;
  }

  .page-title {
    font-size: 2rem;
  }
}
</style>