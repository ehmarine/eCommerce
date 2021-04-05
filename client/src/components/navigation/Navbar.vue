<template>
  <!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-light bg-navbar">
  <!-- Container wrapper -->
  <div class="container">
    <!-- Navbar brand -->
    <router-link class="navbar-brand" to="/">
      <i class="fas fa-store logo"></i> <span class="logotext"> eCommerce</span>  
    </router-link>

    <!-- Toggle button -->
    <button
      class="navbar-toggler"
      type="button"
      data-mdb-toggle="collapse"
      data-mdb-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <i class="fas fa-bars"></i>
    </button>

    <!-- Collapsible wrapper -->
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <!-- Left links -->
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">

        <li class="nav-item">
          <router-link class="nav-link" to="/">Home</router-link>
        </li>

        <li class="nav-item">
          <router-link class="nav-link" to="/products">Products</router-link>
        </li>

        <li class="nav-item">
          <router-link class="nav-link" to="/about">About Us</router-link>
        </li>

      </ul>
      <!-- Left links -->

      <ul class="navbar-nav">
        <!-- Navbar dropdown -->
        <li class="nav-item dropdown me-4">
          <a
            class="nav-link dropdown"
            href="#"
            id="navbarDropdown"
            role="button"
            data-mdb-toggle="dropdown"
            aria-expanded="false"
          >
            <i class="fas fa-shopping-cart"></i>
            <span v-show="cartCount" class="badge rounded-pill badge-notification bg-danger">{{cartCount}}</span>
          </a>

          <ul class="dropdown-menu dropdown-menu-end shopping-cart" aria-labelledby="navbarDropdown">
              <Cart />
          </ul>
        </li>

        <li class="nav-item dropdown">
          <a
            class="nav-link dropdown-toggle"
            href="#"
            id="navbarDropdown"
            role="button"
            data-mdb-toggle="dropdown"
            aria-expanded="false"
          >
            <i class="fas fa-user"></i>
          </a>

          <ul class="dropdown-menu dropdown-menu-end" aria-labelledby="navbarDropdown">
            <div class="p-2 d-flex justify-content-between align-items-center user-settings">
            <div class="ms-2">
              <div class="total-price d-flex align-items-center">
                <p>logged in:</p>
              <span class="ms-1 userName" v-if="loggedIn">{{firstName}} </span>
              </div>
            </div>

            <router-link to="/orders" class="btn btn-info">active orders</router-link>
           </div>
          </ul>
        </li>
        <li class="nav-item" v-if="!loggedIn">
          <router-link class="nav-link" to="/login">Login</router-link>
        </li>
        <li class="nav-item" v-if="loggedIn">
          <a href="#" class="nav-link pb-0" @click="logout">Logout</a>
        </li>
      </ul>
    </div>
    <!-- Collapsible wrapper -->
  </div>
  <!-- Container wrapper -->
</nav>
<!-- Navbar -->
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
import Cart from '../cart/Cart.vue'
export default {
  name: 'Navbar',
  components: {
    Cart
  },
  computed: {
    ...mapGetters(['cartCount', 'loggedIn', 'firstName'])

  },
  methods: {
    ...mapActions(['logout'])
  }
}
</script>

<style scoped>
.bg-navbar {
  background: rgba(9, 9, 63, 0.842); 
  color: #fff
}

.logo {
  padding-right: 1rem;
  color: #fff;
}
.userName {
  font-weight: 800;
}
  .logotext {
  color: #fff;
}
p {
  display: inline-block;
  padding-top: 1rem;
}

.nav-link {
  color: #fff !important;
}

.fa-shopping-cart {
  color: rgba(97, 247, 130, 0.973);
  font-size: 1.5rem;
}
.badge {
  font-size: 1rem;
  
}
.shopping-cart {
  min-width: 453px;
}
.user-settings {
  min-width: 400px;
}
</style>