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
                })
                .catch((error) => {
                    console.error(error);
                });
        },
    },

    created() {

    }
}
</script>

<template>
    <main>
        <SearchBar @movieSearch="searchMovie" />
        <ul v-for="(movie, index) in store.movies">
            <li>
                Titolo: {{ movie.title }}
            </li>
            <li>
                Titolo Originale: {{ movie.original_title }}
            </li>
            <li>
                Lingua: {{ movie.original_language }}
            </li>
            <li>
                Voto: {{ movie.vote_average }}
            </li>
        </ul>
    </main>
</template>

<style scoped></style>