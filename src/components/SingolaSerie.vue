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
    <h5>Voto: {{ convertitoreVoto(voto) }}</h5>
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
  methods: {
    convertitoreVoto(numeroDaConvertire) {
      let votoConvertito = Math.floor((numeroDaConvertire * 5) / 10) + 1;
      return votoConvertito;
    },
  },
};
</script>

<style scoped lang="scss">
#container {
  width: calc(100% / 5);
  background-color: #305c88;
}
#bandiera {
  width: 20px;
}
// h1 {
//   text-align: left;
//   color: #ffffff;
//   font-size: 2em;
//   padding: 20px;
//   padding-left: 0px;
// }
</style>