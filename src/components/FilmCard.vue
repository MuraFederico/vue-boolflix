<template>
  <div class="card-container">
      <div class="title">
          <b>Title:</b>
          <span>{{ film.title }}</span>
      </div>
      <div class="og-title">
          <b>Original Title:</b>
          <span>{{ film.originalTitle }}</span>
      </div>
      <div class="vote">
          <b>Vote:</b>
          <span>{{ film.rating }}</span>
      </div>
      <div class="lang">
          <b>Language:</b>
          <span>{{ film.lang }}</span>
      </div>
  </div>
</template>

<script>
export default {
    name: 'FilmCard',
    props: {
        film: Object,
    }
}
</script>

<style lang="scss" scoped>
    .card-container {
        padding: .5rem;
        margin: 1.5rem;
        display: inline-block;
        background-color: black;
        border: 1px solid white;
        color: white;
    }
</style>