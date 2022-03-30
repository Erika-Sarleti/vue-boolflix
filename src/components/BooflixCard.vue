<template>
  <div>

      <h2>{{info.title}}</h2>
      <h3>{{info.originalTitle}}</h3>
      <div>{{info.language}}</div>
      <div>{{info.rating}}</div>
  </div>
</template>

<script>
export default {
     name: 'BooflixCard',
     props:{
         info: Object,
         
     }
}
</script>

<style>

</style>