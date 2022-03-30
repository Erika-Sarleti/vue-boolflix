<template>
  <div id="app">
    <AppHeader @search="findMovie"/>
    <AppMain/>
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
      apiKey: 'ba3c7b44f63406966919314d1d6a1d9d',
    }
  },
  methods:{
    findMovie(userInput){
      axios.get('https://api.themoviedb.org/3/movie/', {
    params: {
      api_key: this.apiKey,
      language: 'it-IT',
      query: userInput,
    }
  }).then(response => {
    this.movieArr = response.data
  })
    }
  }
}
</script>

<style lang="scss">

</style>
