<template>
  <div id="container">
    <!-- "/icAG01wZyy1ZpS3UEnPReph3jMV.jpg" -->
    <!-- https://image.tmdb.org/t/p/w500/icAG01wZyy1ZpS3UEnPReph3jMV.jpg -->
    <img :src="'https://image.tmdb.org/t/p/w200' + poster" />
    <h2>{{ titolo }}</h2>
    <h4>{{ titoloOriginale }}</h4>
    <h4>{{ lingua }}</h4>
    <h5>{{ voto }}</h5>
  </div>
</template>

<script>
export default {
  name: "SingoloFilm",
  props: {
    titolo: String,
    poster: String,
    titoloOriginale: String,
    lingua: String,
    voto: Number,
  },
};
</script>

<style lang="sass" scoped>
</style>