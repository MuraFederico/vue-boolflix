<template>
  <main>
    <div class="container" v-if="arrFilms.length != 0">
        <h2>Films</h2>
        <div class="container-card">
            <film-card v-for="film in arrFilms" :key="film.id"
            :objCard="film"
            />
        </div>
    </div>
    <!-- <div v-else><h2>Couldn't find any film</h2></div> -->
    
    <div  class="container" v-if="arrSeries.length != 0">
        <h2>Series</h2>
        <div class="container-card">
            <film-card v-for="serie in arrSeries" :key="serie.id"
            :objCard="serie"
            />
        </div>
    </div>
    <!-- <div v-else><h2>Couldn't find any serie </h2></div> -->
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
        background-color: black;
    }
    .container {
        width: 85%;
        margin: 0 auto;
    }
    h2 {
        padding: 3rem;
        color: white;
    }
    .container-card {
        display: flex;
        flex-wrap: wrap;
    }
</style>