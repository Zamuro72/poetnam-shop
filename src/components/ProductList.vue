<template>
  <div class="product-list">
    <ProductCard 
      v-for="(product, index) in products" 
      :key="product.id"
      :product="product"
      :style="{ animationDelay: `${index * 100}ms` }"
    />
  </div>
</template>

<script setup>
import ProductCard from './ProductCard.vue'

defineProps({
  products: {
    type: Array,
    required: true
  }
})
</script>

<style scoped>
.product-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

@media (max-width: 768px) {
  .product-list {
    grid-template-columns: 1fr;
  }
}
</style>