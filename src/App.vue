<template>
  <div id="app">
    <header-notflix @emitFilms="getFilms" @emitSeries="getSeries"/>
    <main-notflix :arrFilms="films"/>
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
          title: film.title,
          originalTitle: film.original_title,
          lang: film.original_language,
          rating: film.vote_average,
        }
      });
    },
    getSeries(arrSeries) {
      this.series = arrSeries.map(film => {
        return {
          id: film.id,
          title: film.name,
          originalTitle: film.original_name,
          lang: film.original_language,
          rating: film.vote_average,
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
