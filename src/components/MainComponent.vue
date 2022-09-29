<template>
  <div>
    <div>
      <!-- {{ copertina.original_title }}
      {{ copertina.release_date }} -->
      <SingoloFilm
        v-for="(copertina, index) in insiemeDeiFilm"
        :key="index"
        :titolo="copertina.title"
        :titoloOriginale="copertina.original_title"
        :lingua="copertina.original_language"
        :voto="copertina.vote_average"
        :poster="copertina.poster_path"
      />
    </div>
  </div>
</template>

<script>
import SingoloFilm from "@/components/SingoloFilm.vue";
export default {
  name: "MainComponent",
  props: {
    insiemeDeiFilm: Array,
  },
  components: {
    SingoloFilm,
  },
};
</script>

<style scoped lang="scss">
</style>