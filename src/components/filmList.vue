<template lang="html">
  <div class="">
    <div v-for="film of allFilms" :key="film.id">
      <h2>{{film.title}}</h2>
      <p>{{film.description}}</p>
      <button @click="handleClick(film)">See film info</button>
    </div>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'filmList',
  // data() {
  //   return{
  //     film: {}
  //   }
  // },
  props: ["allFilms"],
  methods: {
    handleClick(film) {
      eventBus.$emit("selected-film", film);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
