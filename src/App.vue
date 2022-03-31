<template>
  <div id="app">
    <AppHeader @search="findSearch"/>
    <AppMain :arr-movies="movieArr" :arr-series="arrSeries"/>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios'

export default {
  name: 'App',
  components: {
   AppHeader,
   AppMain
  },
  data(){
    return{
      movieArr:[],
      arrSeries:[],
      apiKey: 'ba3c7b44f63406966919314d1d6a1d9d',
      basePath: 'http://image.tmdb.org/t/p/w500/',
      defaultImageUrl: 'https://picsum.photos/id/135/300/300',
      maxRating: 5,
    }
  },
  methods:{
  findSearch(userInput){
    if (userInput != ''){
      const objParams= {
            api_key: this.apiKey,
            language: 'it-IT',
            query: userInput,
      }
      this.apiCall('movie', objParams)
      this.apiCall('tv', objParams)  
      } else{
        this.movieArr= [];
        this.arrSeries
      }
    },
  apiCall(searchType, objParams){
    axios.get(`https://api.themoviedb.org/3/search/${searchType}`,{params: objParams,})
    .then(response =>{
      if (searchType === 'movie') {
        this.movieArr = response.data.results.map((movie) => ({
              id: movie.id,
              title: movie.title,
              originalTitle: movie.original_title,
              language: movie.original_language,
              rating: this.normalizeRating(movie.vote_average),
              maxRating: this.maxRating,
              srcPoster: this.getPosterUrl(this.basePath, movie.poster_path),
            }));
    } else {
        this.arrSeries = response.data.results.map(series =>({
            id: series.id,
          title: series.name,
          originalTitle: series.original_name,
          language: series.original_language,
          rating: this.normalizeRating(series.vote_average),
          maxRating: this.maxRating,
          srcPoster: this.getPosterUrl(this.basePath, series.poster_path),
        }))
      }
    })
  },
  getPosterUrl(basePath, pathOriginal) {
      if (pathOriginal === null) {
        return this.defaultImageUrl;
      }
      return (basePath + pathOriginal);
    },
     normalizeRating(ratingOriginal) {
      return Math.ceil((ratingOriginal * this.maxRating) / 10);
    },
  }
  }
</script>

<style lang="scss">

</style>