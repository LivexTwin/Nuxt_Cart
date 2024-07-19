<template>
  <div class="card">
    <img :src="product.img" :alt="product.title" />
    <div>
      <h3>{{ product.title }}</h3>
      <p>{{ product.description }}</p>
      <pre>{{ product.price }} Silver Coins</pre>
      <button class="btn" @click="addToCart()" :disabled="isPending">
        <span v-show="!isPending">Add to cart</span>
        <span class="spinner" v-show="isPending"
          >Adding

          <Icon name="svg-spinners:3-dots-scale" />
        </span>
      </button>
    </div>
    <CartNotification ref="notification" />
  </div>
</template>

<script setup>
const { product } = defineProps(["product"]);

const cartStore = useCartStore();
const isPending = ref(false);
const notification = ref(null);

const addToCart = async () => {
  isPending.value = true;
  await cartStore.addToCart(product);
  setTimeout(() => {
    isPending.value = false;
  }, 1000);
  notification.value.showNotification();
};
</script>

<style scoped>
.card {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.product-info {
  font-size: var(--size-2xl);
  color: var(--clr-secondary);
}

h3 {
  font-size: var(--size-2xl);
  color: var(--clr-secondary);
}

.spinner {
  display: flex;
  align-items: flex-end;
}
</style>
