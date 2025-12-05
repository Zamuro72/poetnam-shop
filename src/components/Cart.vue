<template>
  <div class="cart-item animate-slideInRight">
    <img :src="item.image" :alt="item.name" class="cart-item-image" />
    
    <div class="cart-item-info">
      <h3 class="cart-item-name">{{ item.name }}</h3>
      <p class="cart-item-price">
        Rp {{ item.price.toLocaleString('id-ID') }}
      </p>
    </div>

    <div class="cart-item-actions">
      <div class="quantity-controls">
        <button @click="decreaseQuantity" class="quantity-btn">
          <Minus :size="20" />
        </button>
        <span class="quantity">{{ item.quantity }}</span>
        <button @click="increaseQuantity" class="quantity-btn quantity-btn-primary">
          <Plus :size="20" />
        </button>
      </div>

      <button @click="removeItem" class="remove-btn">
        <Trash2 :size="20" />
      </button>
    </div>
  </div>
</template>

<script setup>
import { Minus, Plus, Trash2 } from 'lucide-vue-next'
import { useCartStore } from '../store/index.js'

const props = defineProps({
  item: {
    type: Object,
    required: true
  }
})

const cartStore = useCartStore()

const increaseQuantity = () => {
  cartStore.updateQuantity(props.item.id, props.item.quantity + 1)
}

const decreaseQuantity = () => {
  if (props.item.quantity > 1) {
    cartStore.updateQuantity(props.item.id, props.item.quantity - 1)
  }
}

const removeItem = () => {
  cartStore.removeFromCart(props.item.id)
}
</script>

<style scoped>
.cart-item {
  background: white;
  border-radius: 1rem;
  padding: 1.5rem;
  display: flex;
  align-items: center;
  gap: 1.5rem;
  transition: all 0.3s ease;
}

.cart-item:hover {
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

.cart-item-image {
  width: 6rem;
  height: 6rem;
  object-fit: cover;
  border-radius: 0.5rem;
}

.cart-item-info {
  flex: 1;
}

.cart-item-name {
  font-size: 1.25rem;
  font-weight: 700;
  color: #1f2937;
  margin-bottom: 0.5rem;
}

.cart-item-price {
  font-size: 1.125rem;
  font-weight: 700;
  color: #ec4899;
}

.cart-item-actions {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.quantity-controls {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.quantity-btn {
  width: 2.5rem;
  height: 2.5rem;
  background: #e5e7eb;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
}

.quantity-btn:hover {
  background: #d1d5db;
}

.quantity-btn-primary {
  background: #ec4899;
  color: white;
}

.quantity-btn-primary:hover {
  background: #db2777;
}

.quantity {
  font-size: 1.25rem;
  font-weight: 700;
  min-width: 3rem;
  text-align: center;
}

.remove-btn {
  width: 2.5rem;
  height: 2.5rem;
  background: #fee2e2;
  color: #ef4444;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
}

.remove-btn:hover {
  background: #fecaca;
}

@media (max-width: 768px) {
  .cart-item {
    flex-direction: column;
    align-items: flex-start;
  }

  .cart-item-actions {
    width: 100%;
    justify-content: space-between;
  }
}
</style>