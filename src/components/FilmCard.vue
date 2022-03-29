<template>
  <div class="card-container">
      <div class="title">
          <b>Title:</b>
          <span>{{ objCard.title }}</span>
      </div>
      <div class="og-title">
          <b>Original Title:</b>
          <span>{{ objCard.originalTitle }}</span>
      </div>
      <div class="vote">
          <b>Vote:</b>
          <span>{{ objCard.rating }}</span>
      </div>
      <!-- <div class="lang">
          <b>Language:</b>
          <span>{{ objCard.lang }}</span>
      </div> -->
     <lang-flag :iso="objCard.lang"/>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: 'FilmCard',
    components: {
        LangFlag,
    },
    props: {
        objCard: Object,
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