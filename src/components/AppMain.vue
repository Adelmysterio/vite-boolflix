<script>
import { store } from '../store.js';
import axios from 'axios';
import SearchBar from './SearchBar.vue';

export default {

    components: {
        SearchBar,
    },

    data() {
        return {
            store,
        }
    },

    methods: {
        searchMovie(movieName) {
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: 'e99307154c6dfb0b4750f6603256716d',
                    query: movieName
                }
            })
                .then((response) => {
                    console.log(response.data.results);
                    this.store.movies = response.data.results
                    this.searchSeries(movieName)
                })
                .catch((error) => {
                    console.error(error);
                });
        },

        searchSeries(seriesName) {
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: 'e99307154c6dfb0b4750f6603256716d',
                    query: seriesName
                }
            })
                .then((response) => {
                    console.log(response.data.results);
                    this.store.series = response.data.results
                })
                .catch((error) => {
                    console.error(error);
                });
        },
        getFlag(nation) {
            let flag = "https://flagsapi.com/"+ nation + "/flat/16.png"
            if (nation == "EN") {
                flag = "https://flagsapi.com/GB/flat/16.png"
            }
            return flag
        }

    },

    created() {
        
    }
}
</script>

<template>
    <main>
        <SearchBar @movieSearch="searchMovie" />
        <h1>Film</h1>
        <ul v-for="(movie, index) in store.movies">
            <li>
                Titolo: {{ movie.title }}
            </li>
            <li>
                Titolo Originale: {{ movie.original_title }}
            </li>
            <li class="flex-center">
                Lingua: <img :src="getFlag(movie.original_language.toUpperCase())" alt="">
            </li>
            <li>
                Voto: {{ movie.vote_average }}
            </li>
        </ul>
        <h1>Serie TV</h1>
        <ul v-for="(serie, index) in store.series">
            <li>
                Titolo: {{ serie.name }}
            </li>
            <li>
                Titolo Originale: {{ serie.original_name }}
            </li>
            <li class="flex-center">
                Lingua: <img :src="getFlag(serie.original_language.toUpperCase())" alt="">
            </li>
            <li>
                Voto: {{ serie.vote_average }}
            </li>
        </ul>
    </main>
</template>

<style lang="scss" scoped>
@use '../style/general.scss' as *;

h1 {
    margin-bottom: 1rem;
}
</style>