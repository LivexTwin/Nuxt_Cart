<!-- components/CartNotification.vue -->
<template>
  <transition name="slide-down">
    <div v-if="show" class="cart-popup">
      <div class="cart-popup-header">
        <p>Product added to cart!</p>
        <button class="close-btn" @click="hideNotification">
          <Icon class="close-icon" name="ph:x" />
        </button>
      </div>

      <div class="cart-popup-info">
        <div v-for="product in cartStore.cart" :key="product.id">
          <img :src="product.img" :alt="product.title" />
          <p>{{ product.title }}</p>
        </div>
      </div>

      <button class="dismiss-btn" @click="hideNotification">
        Keep Shopping
      </button>
    </div>
  </transition>
</template>

<script setup>
import { ref } from "vue";

const cartStore = useCartStore();
const show = ref(false);

const showNotification = () => {
  show.value = true;
};

const hideNotification = () => {
  show.value = false;
};

defineExpose({ showNotification });
</script>

<style scoped>
.cart-popup {
  position: fixed;
  top: 0;
  right: 0;
  width: 23rem;
  background-color: var(--clr-primary);
  color: white;
  padding: 1rem 1.5rem;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  z-index: 999;
  display: block;
}

.cart-popup-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.close-btn,
.dismiss-btn {
  background: none;
  border: none;
  color: white;
  font-size: 1rem;
  cursor: pointer;
  margin-left: 1rem;
}

.close-btn:hover,
.dismiss-btn:hover {
  text-decoration: underline;
}

.slide-down-enter-active,
.slide-down-leave-active {
  transition: transform 1000ms ease;
}

.slide-down-enter-from,
.slide-down-leave-to {
  transform: translateY(-100%);
}
</style>
