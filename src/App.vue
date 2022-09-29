<template>
  <div id="app">
    <HeaderComponent @ricerca="chooseSerie" />
    <MainComponent :insiemeDeiFilm="movies" :insiemeDelleSerie="series" />
  </div>
</template>

<script>
import axios from "axios";
import HeaderComponent from "@/components/HeaderComponent.vue";
import MainComponent from "@/components/MainComponent.vue";

export default {
  name: "App",
  data() {
    return {
      indirizzoApiFilm:
        "https://api.themoviedb.org/3/search/movie?api_key=a8d67339fa1940339138961de35a981e&language=it-IT&query=",
      indirizzoApiSerie:
        "https://api.themoviedb.org/3/search/tv?api_key=a8d67339fa1940339138961de35a981e&language=it-IT&query=",

      movies: [],
      series: [],
    };
  },
  methods: {
    chooseMovie(testoDaCercare) {
      console.log(testoDaCercare);
      const indirizzoFinale = this.indirizzoApiFilm + testoDaCercare;
      axios
        .get(indirizzoFinale)
        .then(({ status, data }) => {
          if (status === 200) {
            console.log(data);
            this.movies = data.results;
            console.log(this.movies);
            // console.log(data);
          } else {
            console.log(status);
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
    chooseSerie(testoDaCercare) {
      console.log(testoDaCercare);
      const indirizzoFinaleSerie = this.indirizzoApiSerie + testoDaCercare;
      axios
        .get(indirizzoFinaleSerie)
        .then(({ status, data }) => {
          if (status === 200) {
            console.log(data);
            this.series = data.results;
            console.log(this.series);
          } else {
            console.log(status);
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },

  components: {
    HeaderComponent,
    MainComponent,
  },
};
</script>

<style lang="scss">
@import "./assets/style/standard.scss";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #2c3e50;
  // height: 100vh;
}
</style>
