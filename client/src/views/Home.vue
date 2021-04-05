<template>
  <div class="home">
    <div class="welcome">
      <h1 v-if="loggedIn">Welcome back,</h1> <h1 class="userName" v-if="loggedIn" > {{ firstName }} </h1>
      <h1 v-else> Welcome</h1>
    </div>  

    <div class="info d-lg-flex">
      <div class="info-text m-auto">
        <h2>Hey look!</h2>
        <br>
        <h4>A picture with a functional router link straight to the products, just so you can get straight into buyin! <i class="far fa-hand-point-right"></i></h4>
      </div>
      <div>
        <router-link to="/products"> <img src="../assets/images/ecommerce.jpg" alt="ecommerce img"> </router-link>
      </div>  
    </div>
  </div>
    
</template>

<script>
// @ is an alias to /src
import {mapGetters, mapActions} from 'vuex'

export default { 
  name: 'Home',
 
    computed: {
    ...mapGetters(['firstName','loggedIn', 'products'])
  },
  methods: {
    ...mapActions(['getProducts'])
  },
}

</script>


<style scoped>
  .userName {
    font-weight: 800;
  }

  .info-text {
    padding: 0 2rem;
  }
  h2 {
    text-decoration: underline;
  }
  .home {
    min-height: 700px;
  }
  h4 {
    font-style: italic;
  }
  img {
    /* display: block; */
    max-width: 110%;
    height: auto;
  }
  .welcome {
    padding-top: 1rem;
    padding-bottom: 1rem;
    background: rgba(240, 240, 240, 0.466);
  }

</style>