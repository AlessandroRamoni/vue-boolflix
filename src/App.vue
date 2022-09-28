<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent :insiemeDeiFilm="arrayAppoggio" />
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
      indirizzoApi:
        "https://api.themoviedb.org/3/trending/movie/week?api_key=a8d67339fa1940339138961de35a981e&query=back",
      arrayAppoggio: [],
    };
  },
  created() {
    axios
      .get(this.indirizzoApi)
      .then(({ status, data }) => {
        if (status === 200) {
          console.log(data);
          this.arrayAppoggio = data.results;
          console.log(this.arrayAppoggio);
          // console.log(data);
        } else {
          console.log(status);
        }
      })
      .catch((error) => {
        console.log(error);
      });
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
  height: 100vh;
}
</style>
