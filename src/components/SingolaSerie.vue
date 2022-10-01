<template>
  <div id="container">
    <div id="copertina">
      <img :src="'https://image.tmdb.org/t/p/w342' + poster" />
    </div>
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
  position: relative;
  #info-serie {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    background-color: brown;
    height: 344px;
    width: 230px;
    margin-left: 20px;
    margin-top: 20px;
    font-size: 0.7em;
    border: 1px solid white;
    padding: 5px;
    background-color: black;
    color: #ffffff;
  }
  #info-serie:hover {
    cursor: pointer;
    opacity: 1;
  }
  #bandiera {
    width: 20px;
  }
  #stelline {
    color: gold;
  }
}
</style>