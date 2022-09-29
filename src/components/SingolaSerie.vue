<template>
  <div id="container">
    <img :src="'https://image.tmdb.org/t/p/w200' + poster" />
    <h2>Titolo: {{ titolo }}</h2>
    <h4>Titolo originale: {{ titoloOriginale }}</h4>
    <h4>
      Lingua:
      <img
        id="bandiera"
        :src="'https://flagicons.lipis.dev/flags/4x3/' + lingua + '.svg'"
        alt=""
      />
    </h4>
    <h5>Voto: {{ voto }}</h5>
  </div>
</template>

<script>
export default {
  name: "SingolaSerie",
  props: {
    titolo: String,
    poster: String,
    titoloOriginale: String,
    lingua: String,
    voto: Number,
  },
};
</script>

<style scoped lang="scss">
#container #bandiera {
  width: 20px;
}
</style>