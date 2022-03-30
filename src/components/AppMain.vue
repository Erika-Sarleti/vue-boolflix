<template>
  <main>
    <BooflixCard v-for="movie in arrMovies"
    :key='movie.id'
    :info='movie'
    />
  </main>
</template>

<script>
import BooflixCard from './components/BooflixCard.vue';

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