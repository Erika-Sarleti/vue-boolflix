<template>
  <main>
    <h1 v-if='arrMovies != 0'>Film</h1>
    <BooflixCard v-for="movie in arrMovies"
    :key='movie.id'
    :info='movie'
    />
    <h1 v-if='arrMovies != 0'>Serie TV</h1>
    <BooflixCard v-for="series in arrSeries"
    :key='series.id'
    :info='series'
    /> 
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

<style>

</style>