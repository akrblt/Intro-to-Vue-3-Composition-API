<script setup>
import ProductDetails from './ProductDetails.vue'
import {computed,ref} from 'vue'
import socksGreenImage from '../assets/images/socks_green.jpeg'
import socksBlueImage from '../assets/images/socks_blue.jpeg'

const product = ref('Socks')
const brand = ref('CPNV')

// computed property
const producttitle= computed (()=>{
  return `${brand.value} ${product.value}`
})

//const image = ref(socksGreenImage)

const description=ref("These socs are very comportable")
//const inStock = ref(false)
  
const details = ref(['50% cotton', '30% wool', '20% polyester'])

const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage ,quantity:5},
  { id: 2235, color: 'blue', image: socksBlueImage,quantity:10 },
])

const selectedVariant=ref(variants.value[0])
const sizes=ref(['S','M','L','XL'])


const image=computed(()=>selectedVariant.value.image)
const inStock=computed(()=>selectedVariant.value.quantity>0)
const onSale=ref(true)
const sale=computed(()=>{
  return onSale.value ? 'are on sale' : ' are not sale'
})

//const addToCart = () => cart.value += 1

//const updateImage = (variantImage) => image.value = variantImage



const url=ref('https://www.happysocks.com/ch/')

const props=defineProps({
    premium:{
        type:Boolean,
        required:true
    }
})

const shipping=computed(()=>{
    if (props.premium){
        return 'Free'
    }
    return 5.99
})

const emit= defineEmits(['add-to-cart','remove-from-cart'])

function updateVariant(index){
  selectedVariant.value=variants.value[index]
  console.log('Selected variant :' , selectedVariant.value)
}

function addToCart(){
    emit("add-to-cart",selectedVariant.value.id)
  
}

function removeFromcart(){
    
  
  emit("remove-from-cart",selectedVariant.value.id)
}

</script>


<template>


    <div class="product-display">
    <div class="product-container">
      
      <div class="product-info">
        <h1>{{ producttitle }}</h1>
        <p>{{ sale }}</p>
        <p>{{ description }}</p>
        <img v-bind:src="image" :class="{'out-of-stock-img': !inStock}" >
        <button @click="addToCart"
        :disabled="!inStock"
        :class="{disabledButton: !inStock}"
        >Ajouter au panier</button>
        <button @click="removeFromcart">Enlever le panier</button>

      </div>  

      <div class="product-image">    </div>
        
      <h3>Composition</h3>
        
        <ProductDetails :details="details" ></ProductDetails>

        <p>{{ shipping }}</p>
        <h3>Variants</h3>
        <div >
          <ul>
        <li v-for ="(variant , index) in variants" 
        :key="variant.id"
        class="color-circle"
        :style="{backgroundColor:variant.color}"
         @mouseover="updateVariant(index)"
         ></li>
      </ul>
        </div>
        
      <h3>Sizes</h3>
      <ul>
        <li v-for="size in sizes" :key="size">{{ size }}</li>
      </ul>
    </div>
    </div>
</template>