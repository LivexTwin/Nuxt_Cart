<template>
  <div class="product-quantity">
    <button class="btn" @click="cartStore.decQuantity(product)">-</button>
    <p>{{ product.quantity }}</p>
    <button class="btn" @click="cartStore.incQuantity(product)">+</button>
  </div>
</template>

<script setup>
const cartStore = useCartStore();

defineProps(["product"]);
</script>

<style scoped>
.product-quantity {
  display: flex;
}

p {
  background-color: white;
  color: black;
  padding: 0 0.5rem;
}
</style>
