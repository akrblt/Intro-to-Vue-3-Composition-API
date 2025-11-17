<script setup>
import { computed, ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'
import socksBlueImage from './assets/images/socks_blue.jpeg'
import './assets/main.css'


const product = ref('Socks')
//const image = ref(socksGreenImage)
const description=ref("These socs are very comportable")

const cart=ref(0)

//const inStock = ref(true)

const brand=ref('CPNV')


// computed property
const productTitle = computed(() => {
  return `${brand.value} ${product.value}`
})

const url =ref('https://www.happysocks.com/ch/')
const composition =ref(['50% coton ','30% laine','20% polyester'])
const variants=ref([
  {id:1,color:'blue',image:socksBlueImage, quantity:5},
  {id:2,color:'green',image:socksGreenImage,quantity:0}])

const selectedVariant = ref(variants.value[0])

const sizes=ref(['S','M','L','XL'])  

const image=computed(() => selectedVariant.value.image)
const inStock=computed(() => selectedVariant.value.quantity>0)

const onSale =ref(true)

const sale= computed(()=> {
  return onSale.value ? 'est en action' : '' })


function updateVariant(index){
  selectedVariant.value = variants.value[index]
  console.log('Selected variant :' , selectedVariant.value)
}

function addToCart(){
  cart.value++
}

function removeFromCart(){
  if(cart.value > 0) cart.value--
}

//function changeImage(itemPath){
//  image.value=itemPath
//}

</script>
  
<template>
  <div class="nav-bar">
    <p>Panier : {{ cart }}</p>
  </div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <h1>{{ productTitle }}</h1>
        <p>{{ sale }}</p>
        <p>{{ description }}</p>
        <img v-bind:src="image" :class="{'out-of-stock-img': !inStock }">
        <button @click="addToCart"
        :disabled="!inStock"
        :class="{disabledButton: !inStock}"
         >Ajouter au panier</button>
        <button @click="removeFromCart">Enlever du panier</button>
      </div>
      <div class="product-image">    
        
      </div>
      <h3>Composition</h3>
      <ul>
        <li v-for="item in composition" :key="item">
          {{item}}
        </li>
      </ul>
      <h3>Variants</h3>
      <ul>
        <li v-for ="(variant , index) in variants" 
        :key="variant.id"
        class="color-circle"
        :style="{backgroundColor:variant.color}"
         @mouseover="updateVariant(index)"
         ></li>
      </ul>
      <h3>Sizes</h3>
      <ul>
        <li v-for="size in sizes" :key="size">{{size}} </li>
        
        

      </ul>
      
    </div>
  </div>
</template>