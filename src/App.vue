<template>
  <div id="app">
    <h1>Studio Ghibli films</h1>
    <film-list :allFilms = "allFilms"></film-list>
    <film-details v-if="selectedFilm" :selectedFilm = "selectedFilm"></film-details>
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
      // allFilmsSummary: []
      selectedFilm: {}
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
  methods: {
    getFilmSummaries(films) {
      return films.map(function (film) {
        return {'title': film.title, 'description': film.description}
      });
    }
  },
  components: {
    "film-list": filmList,
    'film-details': filmDetails
  }
}
</script>

<style>
  /* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
