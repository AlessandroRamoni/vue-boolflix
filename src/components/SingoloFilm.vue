<template>
  <div id="container">
    <div id="copertina">
      <img :src="'https://image.tmdb.org/t/p/w342' + poster" />
    </div>
    <div id="info-film">
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
        <!-- {{ convertitoreStelle(convertitoreVoto(voto)) }} -->
      </h5>
    </div>
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
    sinossi: String,
  },
  methods: {
    convertitoreVoto(voto) {
      let votoConvertito = Math.floor((voto * 5) / 10) + 1;
      return votoConvertito;
    },
    /*
    convertitoreStelle(numero) {
      let stelline = "";
      switch (numero) {
        case 1:
          stelline =
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>';
          break;
        case 2:
          stelline =
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>';
          break;
        case 3:
          stelline =
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>';
          break;
        case 4:
          stelline =
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-regular fa-star"></font-awesome-icon>';
          break;
        case 5:
          stelline =
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>' +
            '<font-awesome-icon icon="fa-solid fa-star"></font-awesome-icon>';
          break;
      }
      return stelline;
    },
*/
  },
};
</script>

<style scoped lang="scss">
#container {
  width: calc(100% / 5);
  padding: 20px;
  position: relative;
  #bandiera {
    width: 20px;
  }
  #info-film {
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
    overflow: auto;
  }
  #stelline {
    color: gold;
  }
  #info-film:hover {
    opacity: 1;
    cursor: pointer;
  }
}
</style>