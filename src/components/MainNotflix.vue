<template>
  <main>
      <film-card />
  </main>
</template>

<script>
import FilmCard from './FilmCard.vue';

export default {
    name: 'MainNotflix',
    components: {
        FilmCard,
    }
}
</script>

<style>
    main {
        height: 90vh;
        background-color: darkgray;
    }
</style>