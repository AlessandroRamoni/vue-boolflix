<template>
  <div>
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
    <div id="contenitore-trending">
      <EnglishFilms
        v-for="film in filmInInglese"
        :key="film.id"
        :title="film.title"
        :originalTitle="film.original_title"
        :language="film.original_language"
        :vote="film.vote_average"
        :poster="film.poster_path"
        :overview="film.overview"
      />
    </div>
  </div>
</template>

<script>
import SingoloFilm from "@/components/SingoloFilm.vue";
import SingolaSerie from "@/components/SingolaSerie.vue";
import EnglishFilms from "@/components/EnglishFilms.vue";
export default {
  name: "MainComponent",
  props: {
    insiemeDeiFilm: Array,
    insiemeDelleSerie: Array,
    filmInInglese: Array,
  },
  components: {
    SingoloFilm,
    SingolaSerie,
    EnglishFilms,
  },
};
</script>

<style scoped lang="scss">
#contenitore-film,
#contenitore-serie,
#contenitore-trending {
  display: flex;
  flex-wrap: wrap;
}
#contenitore-film,
#contenitore-trending {
  background-color: #2c3e50;
}

#serieTv {
  background-color: #305c88;
}
</style>