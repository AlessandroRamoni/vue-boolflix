<template>
  <div id="container">
    <!-- "/icAG01wZyy1ZpS3UEnPReph3jMV.jpg" -->
    <!-- https://image.tmdb.org/t/p/w500/icAG01wZyy1ZpS3UEnPReph3jMV.jpg -->
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
  name: "SingoloFilm",
  props: {
    titolo: String,
    poster: String,
    titoloOriginale: String,
    lingua: String,
    voto: Number,
  },
  methods: {
    convertitoreVoto(voto) {
      let votoConvertito = (voto * 5) / 10;
      return votoConvertito;
    },
  },
};
</script>

<style scoped lang="scss">
#container {
  width: calc(100% / 5);
  #bandiera {
    width: 20px;
  }
}
</style>