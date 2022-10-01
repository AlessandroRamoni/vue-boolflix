<template>
  <div id="container">
    <img :src="'https://image.tmdb.org/t/p/w342' + poster" />
    <div id="info-serie">
      <h2>Titolo: {{ titolo }}</h2>
      <h4>Titolo originale: {{ titoloOriginale }}</h4>
      <p>Sinossi: {{ sinossi }}</p>
      <h4>
        Lingua:
        <img
          id="bandiera"
          :src="'https://flagicons.lipis.dev/flags/4x3/' + lingua + '.svg'"
          alt=""
        />
      </h4>
      <h5>
        Voto:
        <div id="stelline">
          <font-awesome-icon
            v-for="n in 5"
            :key="n"
            :icon="[
              n <= convertitoreVoto(voto) ? 'fa-solid' : 'fa-regular',
              'fa-star',
            ]"
          />
        </div>
      </h5>
    </div>
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
    sinossi: String,
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
  padding: 20px;
  background-color: #305c88;
  // #info-serie {
  //   display: none;
  // }
  #stelline {
    color: gold;
  }
  :hover {
    cursor: pointer;
  }
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