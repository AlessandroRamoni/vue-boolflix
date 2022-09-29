<template>
  <div>
    <div>
      <SingoloFilm
        v-for="copertina in insiemeDeiFilm"
        :key="copertina.id"
        :titolo="copertina.title"
        :titoloOriginale="copertina.original_title"
        :lingua="copertina.original_language"
        :voto="copertina.vote_average"
        :poster="copertina.poster_path"
      />
    </div>
    <SingolaSerie />
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
</style>