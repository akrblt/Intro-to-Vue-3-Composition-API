<script setup>

const props=defineProps({
    reviews:{
        type:Array,
        required:true
    }
})

</script>

<template>

    <div class="review-container" v-if="props.reviews.length > 0">
        <h3>Commentaires</h3>
        <ul>
            <li v-for="(review,index) in props.reviews" :key="index">
                <p><strong>Nom: </strong>{{ review.name }}</p>
                <p><strong>Commentaire: </strong>{{ review.review }}</p>
                <p><strong>Rating: </strong>{{ review.rating }}</p>
                <p><strong>Recomandé: </strong>{{ review.recommend }}</p>

                
            </li>
        </ul>
        <p v-if="props.reviews.length===0">Pas encore de commentaires.</p>
    </div>
</template>