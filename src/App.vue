<template>
  <div id="app">
    <div id="stars">
      <font-awesome-icon icon="fa-regular fa-star" />
      <font-awesome-icon icon="fa-solid fa-star" />
      <font-awesome-icon icon="fa-regular fa-star" />
      <font-awesome-icon icon="fa-solid fa-star" />
      <font-awesome-icon icon="fa-regular fa-star" />
      <font-awesome-icon icon="fa-solid fa-star" />
      <font-awesome-icon icon="fa-regular fa-star" />
      <font-awesome-icon icon="fa-solid fa-star" />
      <font-awesome-icon icon="fa-regular fa-star" />
      <font-awesome-icon icon="fa-solid fa-star" />
    </div>
    <HeaderComponent @ricerca="choose" />
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
    choose(testoDaCercare) {
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
@import url("https://fonts.googleapis.com/css2?family=Luckiest+Guy&display=swap");
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #2c3e50;
  height: 100vh;
  font-family: "Luckiest Guy", cursive;
  #stars {
    color: gold;
    padding: 5px 0px;
  }
}
</style>
