<template>
  <header>
      <label for="searchbar"></label>
      <input type="text" name="searchbar" v-model="userInput">
      <button @click="$emit('search', userInput )" >Cerca</button>
  </header>
</template>

<script>
export default {
    name: 'AppHeader',

    data(){
        return{
            userInput:'',
        } 
    }
}
</script>

<style>

</style>