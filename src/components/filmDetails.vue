<template lang="html">
  <div id="detail-wrapper">
    <div id="film-detail">
      <h2>{{selectedFilm.title}}, {{selectedFilm.release_date}}</h2>
      <p>{{selectedFilm.description}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["selectedFilm"]
}
</script>

<style lang="css" scoped>

#film-detail {
  width: 20rem;
  padding: 0.5rem;
  border: 0em none;
  border-radius: 2%;
  color: White;
  background-color: Grey;
}

h2 {
  font-size: 1em;
  margin-top: 0em;
}

p {
  font-size: 0.5em;
  line-height: 1.6em;
}

</style>
