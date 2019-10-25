<template>
  <div id="app">
    <h1>Studio Ghibli films</h1>
    <film-list :allFilms = "allFilms"></film-list>
  </div>
</template>

<script>
import filmList from './components/filmList.vue'

export default {
  name: 'app',
  data() {
    return {
      allFilms: [],
      allFilmsSummary: []
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then((rawFilmData) => {
      this.allFilms = rawFilmData
      // ;
      // this.allFilmsSummary = this.getFilmSummaries(this.allFilms)
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
    "film-list": filmList
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
