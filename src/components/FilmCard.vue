<template>
  <div class="card-container">
		<img :src="`https://image.tmdb.org/t/p/w342${objCard.poster}`" :alt="objCard.title">
		<div class="title">
			<b>Title:</b>
			<span>{{ objCard.title }}</span>
		</div>
		<div class="og-title">
			<b>Original Title:</b>
			<span>{{ objCard.originalTitle }}</span>
		</div>
		<!-- <div class="vote">
			<b>Vote:</b>
			<span>{{ objCard.rating }}</span>
		</div> -->
		<font-awesome-icon icon="fa-solid fa-star" v-for="n in 5" :key="n" :class="n <= objCard.rating ? 'yellow' : ''"/>
		<div class="flag">
		<lang-flag :iso="objCard.lang"/>
		</div>
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
	.yellow {
		color: gold;
	}
</style>