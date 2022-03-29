<template>
  <div id="app">
    <header-notflix @emitFilms="getFilms" @emitSeries="getSeries"/>
    <main-notflix :arrFilms="films" :arrSeries="series"/>
  </div>
</template>

<script>
import HeaderNotflix from './components/HeaderNotflix.vue';
import MainNotflix from './components/MainNotflix.vue';

export default {
  name: 'App',
  components: {
    HeaderNotflix,
    MainNotflix,
  },
  data() {
    return {
      films: [],
      series: [],
    }
  },
  methods: {
    getFilms(arrFilms) {
      this.films = arrFilms.map(film => {
        return {
          id: film.id,
          poster: film.poster_path,
          title: film.title,
          originalTitle: film.original_title,
          lang: film.original_language,
          rating: film.vote_average,
        }
      });
    },
    getSeries(arrSeries) {
      this.series = arrSeries.map(serie => {
        return {
          id: serie.id,
          poster: serie.poster_path,
          title: serie.name,
          originalTitle: serie.original_name,
          lang: serie.original_language,
          rating: serie.vote_average,
        }
      });
    }
  },
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
</style>
