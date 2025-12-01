<script setup>
import { computed, ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'
import socksBlueImage from './assets/images/socks_blue.jpeg'
import ProductDisplay from './composents/ProductDisplay.vue';

const cart = ref([])
const premium=ref(true)
const updateCart=(id)=>{
  cart.value.push(id)
}

const removeFromcart=(id)=>{
  const index=cart.value.indexOf(id);
  console.log(index);
  if(index !== -1){
    cart.value.splice(index,1)
  }
}

</script>
  
<template>
  <div class="nav-bar">
    <p>Panier : {{ cart }}</p>
  </div>
  <div class="cart">Cart({{ cart }})</div>

  <ProductDisplay :premium="premium" @add-to-cart="updateCart" @remove-from-cart="removeFromcart"></ProductDisplay>

  
  
</template>