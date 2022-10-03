<template>
  <div>
    <!-- <h1>Film</h1> -->
    <div id="contenitore-film">
      <SingoloFilm
        v-for="copertina in insiemeDeiFilm"
        :key="copertina.id"
        :titolo="copertina.title"
        :titoloOriginale="copertina.original_title"
        :lingua="copertina.original_language"
        :voto="copertina.vote_average"
        :poster="copertina.poster_path"
        :sinossi="copertina.overview"
      />
    </div>
    <!-- <h1 id="serieTv">Serie TV</h1> -->
    <div id="contenitore-serie">
      <SingolaSerie
        v-for="serieTv in insiemeDelleSerie"
        :key="serieTv.id"
        :titolo="serieTv.name"
        :titoloOriginale="serieTv.original_name"
        :lingua="serieTv.original_language"
        :voto="serieTv.vote_average"
        :poster="serieTv.poster_path"
        :sinossi="serieTv.overview"
      />
    </div>
  </div>
</template>

<script>
import SingoloFilm from "@/components/SingoloFilm.vue";
import SingolaSerie from "@/components/SingolaSerie.vue";
export default {
  name: "MainComponent",
  props: {
    insiemeDeiFilm: Array,
    insiemeDelleSerie: Array,
  },
  components: {
    SingoloFilm,
    SingolaSerie,
  },
};
</script>

<style scoped lang="scss">
#contenitore-film,
#contenitore-serie {
  display: flex;
  flex-wrap: wrap;
}
#contenitore-film {
  background-color: #2c3e50;
}
h1 {
  color: gold;
  font-size: 1.3em;
  padding-top: 15px;
}
#serieTv {
  background-color: #305c88;
}
</style>