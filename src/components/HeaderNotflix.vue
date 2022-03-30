<template>
  <header>
      <h1>BOOLFLIX</h1>
      <nav>
          <input @keyup.enter="getSearch" v-model="strSearch" type="text" placeholder="Search by Name">
          <button @click="getSearch">Cerca</button>
      </nav>
  </header>
</template>

<script>
import axios from 'axios';

export default {
    name: 'HeaderNotflix',
    data() {
        return {
            strSearch: '',
            btnSearchPressed: false,
        };
    },
    methods: {
        formatStr(str) {
            return str.replaceAll(' ', '+')
        },
        getSearch() {
            if (this.strSearch != '') {
                axios.get(`https://api.themoviedb.org/3/search/movie?api_key=1814a5181699a3f32f15c63dc0665bd9&query=${this.formatStr(this.strSearch)}`)
                .then(res => {
                    console.log(res);
                    this.$emit('emitFilms', res.data.results);
                });
                axios.get(`https://api.themoviedb.org/3/search/tv?api_key=1814a5181699a3f32f15c63dc0665bd9&query=${this.formatStr(this.strSearch)}`)
                .then(res => {
                    // console.log(res.data.results);
                    this.$emit('emitSeries', res.data.results);
                });
                this.btnSearchPressed = true;
                this.$emit('emitClickState', this.btnSearchPressed);
                this.strSearch = '';
            }
        },
    },
}
</script>

<style lang="scss" scoped>
    header {
        padding: 1.5rem;
        display: flex;
        justify-content: space-between;
        background-color: black;
        h1 {
            color: red;
        }
        input {
            padding: 1rem;
            margin-right: .5rem;
            &:focus{
                outline: none;
                border:2px solid red;
                border-radius: .3rem;
            }
        }
        button {
            padding: 1rem;
            background-color: red;
            border: none;
            border-radius: .2rem;
        }
    }
</style>>