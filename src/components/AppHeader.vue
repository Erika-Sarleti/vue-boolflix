<template>
  <header>
      <h1 class="app-title">Booflix</h1>
      <form @submit.prevent="$emit('search', userInput )">
        <label for="searchbar"></label>
        <input type="text" name="searchbar" placeholder="Ricerca" v-model="userInput">
      </form>
      
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

<style scoped lang='scss'>
header{
    display: flex;
    justify-content: space-between;
    padding: 1.5rem;
    align-items: center;
    background-color: black;
    color: red;
    h1{
        text-transform: uppercase;
    }
    input{
        height: 2rem;
        width: 250px;
    }
}

</style>