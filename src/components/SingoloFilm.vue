<template>
  <div id="container">
    <img :src="'https://image.tmdb.org/t/p/w200' + poster" />
    <div id="info-film">
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
      <h5>
        Voto:
        <font-awesome-icon
          v-for="n in 5"
          :key="n"
          :icon="[
            n <= convertitoreVoto(voto) ? 'fa-solid' : 'fa-regular',
            'fa-star',
          ]"
        />
        <!-- <i
          v-for="n in 5"
          :key="n"
          class="fa-star"
          :class="n <= convertitoreVoto(voto) ? 'fa-regular' : 'fa-solid'"
        ></i> -->
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
  #bandiera {
    width: 20px;
  }
  // #info-film {
  //   display: none;
  // }
  :hover {
    cursor: pointer;
  }
}
// h1 {
//   text-align: left;
//   color: #ffffff;
//   font-size: 2em;
//   padding: 20px;
//   padding-left: 0px;
// }
</style>