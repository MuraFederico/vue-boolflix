<template>
  <div class="card-container">
		<div class="card-inner">
			<div class="front">
				<img :src="`https://image.tmdb.org/t/p/w342${objCard.poster}`" :alt="objCard.title">
			</div>
			<div class="back">
				<div class="title">
					<b>Title:</b>
					<span>{{ objCard.title }}</span>
				</div>
				<div v-if="objCard.title != objCard.originalTitle" class="og-title">
					<b>Original Title:</b>
					<span>{{ objCard.originalTitle }}</span>
				</div>
				<div class="overview">
					<b>Overview:</b>
					<span>{{ objCard.overview }}</span>
				</div>
				<font-awesome-icon icon="fa-solid fa-star" v-for="n in 5" :key="n" :class="n <= objCard.rating ? 'yellow' : ''"/>
				<div class="flag">
					<lang-flag :iso="objCard.lang"/>
				</div>
			</div>
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
		width: 360px;
		height: 520px;
        margin: 1.5rem;
        color: white;
		perspective: 1000px;
    }
	.card-inner {
		position: relative;
		width: 100%;
		height: 100%;
		// text-align: center;
		transition: transform 0.8s;
		transform-style: preserve-3d;
	}
	.card-container:hover .card-inner {
		transform: rotateY(180deg);
		cursor: pointer;
	}
	.front,
	.back {
		position: absolute;
		width: 100%;
		height: 100%;
		-webkit-backface-visibility: hidden; /* Safari */
		backface-visibility: hidden;
	}
	.front {
		color: white;
	}
	.back {
        padding: 1.5rem;
		background-color: black;
		border: 1px solid white;
		color: white;
		overflow: auto;
		transform: rotateY(180deg);
		div {
			margin-bottom: 1rem;
		}
	}
	.yellow {
		color: gold;
	}
</style>