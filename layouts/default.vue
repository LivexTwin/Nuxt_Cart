<template>
  <header class="wrapper">
    <div class="nav">
      <NuxtLink to="/"><h1>Adventure Store</h1></NuxtLink>
      <NuxtLink to="/cart">
        <Icon name="ph:handbag" size="3em" />
        <span v-if="cartStore.cart.length > 0" class="badge">{{
          cartStore.numberOfProducts
        }}</span>
      </NuxtLink>
    </div>
  </header>

  <div class="wrapper">
    <slot />
  </div>
</template>

<script setup>
// import { useCartStore } from "~/stores/cartStore";

const cartStore = useCartStore();

cartStore.getCart();
</script>

<style scoped>
.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h1 {
  color: var(--clr-secondary);
  font-size: var(--size-5xl);
}

:where(.i-ph\:handbag) {
  background-color: var(--clr-secondary);
}

.badge {
  position: relative;
  top: -2rem;
  left: -15px;
  background-color: white;
  padding: 0.25rem 0.55rem;
  border-radius: 50%;
  font-weight: 900;
}
</style>
