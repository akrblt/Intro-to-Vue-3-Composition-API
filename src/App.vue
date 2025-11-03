<script setup>
import { ref } from 'vue'
import imageGreen from './assets/images/socks_green.jpeg'
import imageBlue from './assets/images/socks_blue.jpeg'

const product = ref('Socks')
const description= ref('These socks are very comportable')
const url=ref('https://www.happysocks.com/ch/')

const inStock=ref(true)
const inventory =ref(5)
const onSale=ref(true)
</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p>{{description}}</p>
        
      </div>
      <div class="product-image">
        <img :src ="imageGreen" width="150">
        <img :src ="imageBlue" width="150">
        <p v-if="inStock">En Stock </p>
        <p v-else="inStock" >En rupture de stock </p>
        <p v-show="inStock">[v-show] Le produit disponible </p> 
        <p>
          <span v-if="inventory > 10">En stock</span>
          <span v-else-if ="inventory >0"> Faible stock</span>
          <span v-else="inventory "> En rupture de stock</span>


        </p>
        <p v-if="onSale" class="sale">Sale</p>
        <a :href ="url" target="_blank"> Visit our store </a>
      </div>
      
    </div>
  </div>
</template>

<style>
.product-display{
  text-align:center;
  margin-top:40px;
}
.sale {
  color:red;
  font-weight: bold;

}
</style>