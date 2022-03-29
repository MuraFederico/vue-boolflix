<template>
  <main>
      <h2>Films</h2>
      <film-card v-for="film in arrFilms" :key="film.id"
      :objCard="film"
      />
      <h2>Series</h2>
      
  </main>
</template>

<script>
import FilmCard from './FilmCard.vue';

export default {
    name: 'MainNotflix',
    components: {
        FilmCard,
    },
    props: {
        arrFilms: Array,
    }
}
</script>

<style>
    main {
        height: 90vh;
        background-color: darkgray;
    }
</style>