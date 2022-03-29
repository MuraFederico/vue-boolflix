<template>
  <main>
      <film-card v-for="film in arrFilms" :key="film.id"
      :film="film"
      />
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