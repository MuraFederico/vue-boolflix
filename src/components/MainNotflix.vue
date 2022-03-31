<template>
  <main>
    <div v-if="btnSearchPressed">
        <div v-if="arrFilms.length == 0 && btnSearchPressed"><h2>Couldn't find any film</h2></div>
        <div class="container" v-else>
            <h2>Films</h2>
            <select name="filter-film" id="filter-film" v-model="selectedFilmGenre">
                <option value="">All</option>
                <option v-for="genre in arrGenreFilms" :key="genre.id" :value="genre.id">{{ genre.name }}</option>
            </select>
            <div class="container-card">
                <film-card v-for="film in filter(arrFilms, selectedFilmGenre)" :key="film.id"
                :objCard="film"
                :arrGenreFilms="arrGenreFilms"
                objType="film"
                />
            </div>
        </div>

        <div v-if="arrFilms.length == 0 && btnSearchPressed"><h2>Couldn't find any serie </h2></div>
        <div  class="container" v-else>
            <h2>Series</h2>
            <select name="filter-Serie" id="filter-Serie" v-model="selectedSerieGenre">
                <option value="">All</option>
                <option v-for="genre in arrGenreSeries" :key="genre.id" :value="genre.id">{{ genre.name }}</option>
            </select>
            <div class="container-card">
                <film-card v-for="serie in filter(arrSeries, selectedSerieGenre)" :key="serie.id"
                :objCard="serie"
                :arrGenreSeries="arrGenreSeries"
                objType="serie"
                />
            </div>
        </div>
    </div>
  </main>
</template>

<script>
import FilmCard from './FilmCard.vue';
import axios from 'axios';

export default {
    name: 'MainNotflix',
    components: {
        FilmCard,
    },
    data() {
        return {
            arrGenreFilms: [],
            arrGenreSeries: [],
            selectedFilmGenre: '',
            selectedSerieGenre: '',
        }
    },
    props: {
        arrFilms: Array,
        arrSeries: Array,
        btnSearchPressed: Boolean,
    },
    created() {
        axios.get('https://api.themoviedb.org/3/genre/movie/list?api_key=1814a5181699a3f32f15c63dc0665bd9')
        .then(res => {
            this.arrGenreFilms = res.data.genres;
        });
        axios.get('https://api.themoviedb.org/3/genre/tv/list?api_key=1814a5181699a3f32f15c63dc0665bd9')
        .then(res => {
            this.arrGenreSeries = res.data.genres;
        });
    },
    //se uso computed mi da un errore//
    methods: {
        filter(arrToFilter, selectedGenre) {
            if (selectedGenre === '') {
                return arrToFilter
            } else {
                return arrToFilter.filter(ele => ele.genres.includes(selectedGenre))
            }
        },
    },
    updated() {
        
    }
}
</script>

<style lang="scss" scoped>
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