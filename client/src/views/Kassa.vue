<template>
  <div class="kassa">
    <div v-for="item in cart" :key="item.product._id">
      <div class="card">

      <div class="card-body">
      <img
        :src="item.product.image"
        class="card-img-top size"
        alt="..."
      />    
        <h5 class="card-title">{{item.product.name}}</h5>
        <p class="card-text short">{{item.product.short}}</p>
        <p class="card-text">Quantity: {{item.quantity}}</p>
        <a href="#!" class="btn btn-danger" @click="deleteItem">DELETE</a>
      </div>
    </div>
  </div>
  <div class="checkout">
    <button class="btn btn-info" @click="handleSave">Place Order</button>
  </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
export default {
  computed: {
    ...mapGetters(['cart', 'totalPrice'])
  },
  methods: {
    ...mapActions(['handleSave', 'deleteItem'])
  }
}
</script>

<style scoped>
.card-body {
  border-bottom: 1px solid rgba(128, 128, 128, 0.384);
  margin-bottom: 1.6rem;
}
.cart {
  min-height: 60vh
}
.kassa {
  min-height: 100vh;
}
img{
  max-width: 200px;
}
.short {
  font-style: italic;
}
</style>