<template lang="html">
  <div id="list-wrapper">
    <div v-for="film of allFilms" :key="film.id">
      <button @click="handleClick(film)">{{film.title}}</button>
    </div>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'filmList',
  props: ["allFilms"],
  methods: {
    handleClick(selectedFilm) {
      eventBus.$emit("selected-film", selectedFilm);
    }
  }
}
</script>

<style lang="css" scoped>

#list-wrapper {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  width: 14rem;
}

button {
  margin: 0.2rem 0.2rem 0rem 0rem;
  border: 0em none;
  border-radius: 3%;
  width: 6rem;
  height: 1.5rem;
  font-size: 0.5em;
  color: White;
  background-color: Green;
  text-align: center;
}

</style>
