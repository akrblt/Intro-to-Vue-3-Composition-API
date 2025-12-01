<script setup>

import {reactive, ref} from "vue"

//const name=ref("")
//const review=ref("")
//const rating=ref(null)
//const recommend=ref("")

const emit = defineEmits(["review-submitted"])
const form = reactive({
    name : "",
    review :"",
    rating : null,
    recommend :"Yes"
})

function onSubmit (){

    if(!form.name || !form.review || !form.rating || !form.recommend){
        alert ("Un des champs est vide. Veuillez indiquer votre nom , votre avis et une note")
        return
    }
//    const productReview ={
//        name : name.value,
//        review : review.value,
//        rating : rating.value,
//        recommend : recommend.value
  //  }

  const productReview ={...form}
    emit("review-submitted",productReview)
    form.name=""
    form.review=""
    form.rating=null
    form.recommend="Yes"

}




</script>

<template>

    <form class="review-form" @submit.prevent="onSubmit">
      <h3>Laissez un commentaire</h3>
      <label for="name">Nom:</label>
      <input id="name" v-model="form.name">
  
      <label for="review">Commentaire:</label>      
      <textarea id="review" v-model="form.review"></textarea>
  
      <label for="rating">Note:</label>
      <select id="rating" v-model.number="form.rating">
        <option>5</option>
        <option>4</option>
        <option>3</option>
        <option>2</option>
        <option>1</option>
      </select>

      
       <label for="recommend">Recommanderiez-vous ce produit ?</label>
       <select  id="recommend" v-model="form.recommend">
        <option >Yes</option>
        <option >No</option>
       </select>
  

      
      
      <input class="button" type="submit" value="Valider">
    </form>



</template>