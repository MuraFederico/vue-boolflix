<template>
  <div id="app">
    <header-notflix @emitFilms="getFilms"/>
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
      console.log(arrFilms)
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
