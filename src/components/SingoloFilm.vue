<template>
  <div id="container">
    <div id="copertina">
      <img :src="getImage(poster)" />
    </div>
    <div id="info-film">
      <h2>Titolo: {{ titolo }}</h2>
      <h4>Titolo originale: {{ titoloOriginale }}</h4>
      <p>Sinossi: {{ sinossi }}</p>
      <h4 id="lingua">
        Lingua:
        <img id="bandiera" :src="getFlags(lingua)" alt="" />
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
    getFlags(paese) {
      switch (paese) {
        case "en": {
          paese = "gb";
          break;
        }
        case "ja": {
          paese = "jp";
          break;
        }
        case "ko": {
          paese = "kr";
          break;
        }
        case "zh": {
          paese = "cn";
          break;
        }
      }
      return `https://flagicons.lipis.dev/flags/1x1/${paese}.svg`;
    },
    getImage(parametro) {
      let fileNotFound =
        "https://thumbs.dreamstime.com/b/error-page-funny-spider-inside-phone-error-page-funny-spider-inside-phone-display-spider-says-sorry-page-not-found-page-161850445.jpg";
      if (parametro === null) {
        parametro = fileNotFound;
        return fileNotFound;
      }
      return `https://image.tmdb.org/t/p/w342${parametro}`;
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
  #copertina {
    border: 2px solid black;
  }
  #copertina img {
    display: block;
    width: 230px;
    height: 340px;
  }
  #bandiera {
    width: 20px;
    height: 15px;
  }
  #info-film {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    background-color: brown;
    height: 344px;
    max-width: 230px;
    margin-left: 20px;
    margin-top: 20px;
    font-size: 0.9em;
    border: 1px solid white;
    padding: 5px;
    background-color: rgb(2, 16, 80);
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