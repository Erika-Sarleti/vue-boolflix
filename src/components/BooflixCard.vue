<template>
  <div class='card-container'>
    <img :src="info.srcPoster" alt="">
    <div class="card-info">
      <h2>{{info.title}}</h2>
      <h3>{{info.originalTitle}}</h3>   
      <div class="language" >{{info.language}}</div>
      <div v-for='stars in info.rating' :key="stars" class="fas fa-star" ></div>
      <div v-for='stars in (info.maxRating - info.rating) ' :key="'vuoti' + stars" class="fa-regular fa-star" ></div>
    </div>
    
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

<style scoped lang='scss'>
.card-container{
  margin: 1em 2em;
  position: relative;
  .card-info{
    position: absolute;
    top: 1em;
    left: 1em;
    display: none;
    
  }
  .card-info:hover{
      display: block;
  }
}

</style>