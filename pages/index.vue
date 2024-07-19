<template>
  <div>
    <h2>All Products</h2>
    <div class="product-grid">
      <div v-for="product in products">
        <ProductCard :product="product" />
      </div>
    </div>
  </div>
</template>

<script setup>
// fetch products
const { data: products } = await useFetch("http://localhost:4000/products");
</script>

<style scoped>
.product-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
</style>
