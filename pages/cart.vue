<template>
  <div>
    <h2>Your basket</h2>

    <div class="card" v-if="cartStore.cart.length">
      <!-- product list -->
      <div class="cart-content" v-for="product in cartStore.cart">
        <img :src="product.img" :alt="product.title" />
        <p>{{ product.title }}</p>
        <!-- product quantity -->
        <ProductQuantity :product="product" />
        <pre>{{ product.price * product.quantity }} silver coins</pre>

        <!-- delete -->
        <button @click="cartStore.deleteFromCart(product)">
          <Icon id="delete-icon" name="ph:trash-simple" />
        </button>
      </div>
      <!-- cart total -->
      <div class="cart-total">
        <span>total amount to pay: </span>
        <span id="total">{{ cartStore.cartTotal }}</span>
      </div>
    </div>

    <div v-else>
      <p>There are no items in your basket.</p>
    </div>
  </div>
</template>

<script setup>
const cartStore = useCartStore();
</script>

<style scoped>
.cart-content {
  display: flex;
  gap: 1.5rem;
  align-items: center;
  text-wrap: nowrap;
}

img {
  margin-left: -0.5rem;
}

.cart-total {
  text-align: right;
  padding-top: 1rem;
  margin-top: 1rem;
  border-top: 2px solid lightgray;
  color: lightgray;
}

#delete-icon {
  color: lightgray;
  font-size: var(--size-md);
  margin-top: 0.55rem;
}

#total {
  color: var(--clr-secondary);
}
</style>
