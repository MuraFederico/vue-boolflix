<template>
  <main>
    <div v-if="arrFilms.length != 0">
        <h2>Films</h2>
        <film-card v-for="film in arrFilms" :key="film.id"
        :objCard="film"
        />
    </div>
    <div v-if="arrSeries.length != 0">
        <h2>Series</h2>
        <film-card v-for="serie in arrSeries" :key="serie.id"
        :objCard="serie"
        />
    </div>
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
        arrSeries: Array,
    }
}
</script>

<style>
    main {
        min-height: 90vh;
        background-color: darkgray;
    }
</style>