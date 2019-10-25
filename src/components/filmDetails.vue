<template lang="html">
  <div class="">
    <h3>{{selectedFilm.title}}</h3>
    <p>{{selectedFilm.release_date}}</p>
    <p>{{selectedFilm.description}}</p>
  </div>
</template>

<script>
export default {
  props: ["selectedFilm"]
}
</script>

<style lang="css" scoped>
</style>
