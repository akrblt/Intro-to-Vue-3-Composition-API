<script setup>
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)
const description=ref("These socs are very comportable")
const url =ref('https://www.happysocks.com/ch/')
const composition =ref(['50% coton ','30% laine','20% polyester'])
const variants=ref([
  {id:1,color:'blue'},
  {id:2,color:'green'}])
const sizes=ref(['S','M','L','XL'])  
</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <h1>{{ product }}</h1>
      </div>
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <h3>Composition</h3>
      <ul>
        <li v-for="item in composition" :key="item">
          {{item}}
        </li>
      </ul>
      <h3>Variants</h3>
      <ul>
        <li v-for ="variant in variants" :key="variant.id">{{variant.color}}</li>
      </ul>
      <h3>Sizes</h3>
      <ul>
        <li v-for="size in sizes" :key="size">{{size}} </li>
        
        

      </ul>
      
    </div>
  </div>
</template>