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
              rating: movie.vote_average,
            }));
    } else {
        this.arrSeries = response.data.results.map(series =>({
            id: series.id,
          title: series.name,
          originalTitle: series.original_name,
          language: series.original_language,
          rating: series.vote_average,
        }))
      }
    })
  },
  }
  }
</script>

<style lang="scss">

</style>