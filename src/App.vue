<script setup>
import { ref } from 'vue'
import imageB from './assets/images/socks_blue.jpeg'
import imageG from './assets/images/socks_green.jpeg'
const product = ref('Socks')
const decsription =ref("These socks are very comportable")

const url=ref('https://www.happysocks.com/ch/')

</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p>{{decsription}} </p>
        <div class="image">
          <img :src="imageB"/>
        <img :src='imageG'/>
        </div>
        <a :href="url" target="_blank"> Visit our store</a>
        
      </div>
    </div>
  </div>
</template>