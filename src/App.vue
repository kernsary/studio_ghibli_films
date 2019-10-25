<template>
  <div id="app">
    <h1>Studio Ghibli films</h1>
    <div id="content-wrapper">
      <film-list :allFilms = "allFilms"></film-list>
      <film-details v-if="selectedFilm" :selectedFilm = "selectedFilm"></film-details>
    </div>
  </div>
</template>

<script>
import filmList from './components/filmList.vue'
import filmDetails from './components/filmDetails.vue'
import {eventBus} from './main.js'

export default {
  name: 'app',
  data() {
    return {
      allFilms: [],
      selectedFilm: null
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then((rawFilmData) => {
      this.allFilms = rawFilmData
    })

    eventBus.$on('selected-film', (selectedFilm) => {
      this.selectedFilm = selectedFilm
    })
  },
  components: {
    "film-list": filmList,
    'film-details': filmDetails
  }
}
</script>

<style>

body {
  font-family: Arial, sans-serif;
}

h1, h2 {
  font-family: "Lucida Grande", sans-serif;
}

h1 {
  margin-bottom: 0.4rem;
}

#content-wrapper {
  display: flex;
}

</style>
