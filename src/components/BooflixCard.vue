<template>
  <div class='card-container'>

      <h2>{{info.title}}</h2>
      <h3>{{info.originalTitle}}</h3>
      <img :src="info.srcPoster" alt="">
      <div class="language" >{{info.language}}</div>
      <div v-for='stars in info.rating' :key="stars" class="fas fa-star" ></div>
      <div v-for='stars in (info.maxRating - info.rating) ' :key="'vuoti' + stars" class="fa-regular fa-star" ></div>
  </div>
</template>

<script>
export default {
     name: 'BooflixCard',
     props:{
         info: Object,
         
     },
}
</script>

<style>


</style>