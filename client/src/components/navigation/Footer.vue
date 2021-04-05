<template>
  <div class="card bg-navbar">
  <div class="card-footer shadow"> 
    <img src="../../assets/images/footer.png" alt="Reklam">
  </div>
  
  <div class="card-body">
    <div class="dropdown">
  <router-link to="/kassa" class="btn btn-success dropdown-toggle" href="#" role="button" id="dropdownMenuLink" data-bs-toggle="dropdown" aria-expanded="false">
    To Checkout <i class="fas fa-shopping-cart"> </i> 
  </router-link>


</div>
<br>
<div>&copy; {{ new Date().getFullYear() }} eCommerce</div>
</div>
</div>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style> 

.card-footer {
background: rgba(255, 255, 255, 0.438); 
}
.bg-navbar {
  background: rgba(9, 9, 63, 0.842); 
  color: #fff
}
</style>