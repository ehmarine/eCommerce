<template>
<div class="container orders">
 
  <div v-for="order in orders" :key="order.index">
    <div class="container border">
      <h6 class="text-start text-muted">Order#</h6>
    <Order v-for="item in order" :key="item.index" :item="item"/>
    </div>
  </div>
  <div v-if="!orders.length">
    <h1>No active orders</h1>
  </div>
  <div class="total">
    <h4>total is: ${{ totalPrice }}</h4>
  </div>
</div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
import Order from '../components/orders/Order'
export default {
  components: {
    Order
  },
  computed: {
    ...mapGetters(['orders','cart','totalPrice'])
  },
  methods: {
    ...mapActions(['getOrders', 'cleanup'])
  },
  created() {

    this.getOrders(sessionStorage.getItem('storedEmail'))
  },
  destroyed() {
    this.cleanup()
    //Städar arrayen vid sidbyte
  }
}
</script>

<style>
.orders {
  min-height: 100vh;
}
.total {
  padding: 1rem;
}
</style>