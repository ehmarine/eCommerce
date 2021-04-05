<template>
<div class="container">
  <div class="card details">
    <h1>Product details</h1>
    <h3>{{ product.name }}</h3>
    <span>"{{ product.short }}"</span>
    <p>{{ product.desc }}</p>
    <img :src="product.image" alt="" class="image-width">
    <p class="price">${{ product.price }}</p>
    </div>
    <button class="btn m-3" @click="addItemToCart({product, quantity})">Add to Cart</button>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
export default {
  data() {
    return {
      quantity: 1
    }
  },
  computed: {
    ...mapGetters(['product']),
  },
  methods: {
    ...mapActions(['getProduct', 'addItemToCart']),
  },
  mounted() {
    this.getProduct(this.$route.params.id)
  },
};
</script>

<style scoped>
.image-width {
  max-width: 600px;
  margin: auto;
}
.price {
  color: rgb(29, 29, 131);
  font-weight: 800;
}
.btn {
  width: 150px;
  background-color: green;
  color: white;
}

span {
  font-style: italic;
  padding-bottom: 1.5rem;
}
</style>
