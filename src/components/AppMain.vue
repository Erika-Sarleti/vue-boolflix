<template>
  <main>
    <h2 v-if='arrMovies != 0'>Film</h2>
    <div class="list-container">
      <BooflixCard v-for="movie in arrMovies"
      :key='movie.id'
      :info='movie'
      />
    </div>
    <h2 v-if='arrMovies != 0'>Serie TV</h2>
    <div class="list-container">
      <BooflixCard v-for="series in arrSeries"
      :key='series.id'
      :info='series'
      /> 
    </div>
    
    
  </main>
</template>

<script>
import BooflixCard from '@/components/BooflixCard.vue';

export default {
    name: 'AppMain',
    components:{
      BooflixCard,
    },
    props:{
      arrMovies: Array,
      arrSeries: Array,
    },
      
}
</script>

<style scoped lang='scss'>
h2{
  margin: 2rem auto;
  color: white;
  text-transform: uppercase;
}
.list-container{
  display: flex;
  flex-wrap: wrap;
}
</style>