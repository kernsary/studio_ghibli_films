<template lang="html">
  <div class="">
    <div v-for="film of allFilms" :key="film.id">
      <h2>{{film.title}}</h2>
      <p>{{film.description}}</p>
    </div>
  </div>
</template>

<script>


export default {
  props: ["allFilms"]
}
</script>

<style lang="css" scoped>
</style>
