<template>
  <div id="container">
    <div id="copertina">
      <img :src="getImage(poster)" />
    </div>
    <div id="info-film">
      <h2>Title: {{ title }}</h2>
      <h4>Original title: {{ originalTitle }}</h4>
      <p>Overview: {{ overview }}</p>
      <h4 id="lingua">
        Language:
        <img id="bandiera" :src="getFlags(language)" alt="" />
      </h4>
      <h5>
        Vote:
        <div id="stelline">
          <font-awesome-icon
            v-for="n in 5"
            :key="n"
            :icon="[
              n <= convertitoreVoto(vote) ? 'fa-solid' : 'fa-regular',
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
  name: "EnglishFilms",
  props: {
    title: String,
    poster: String,
    originalTitle: String,
    language: String,
    vote: Number,
    overview: String,
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