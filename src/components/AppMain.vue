<script>
import { store } from '../store.js';
import axios from 'axios';
export default {
    data() {
        return {
            store,
        }
    },
    methods: {
        searchMovie() {
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: 'e99307154c6dfb0b4750f6603256716d',
                    query: 'john'
                }
            })
                .then((response) => {
                    console.log(response.data.results);
                })
                .catch((error) => {
                    console.error(error);
                });
        },
    },
    created() {
        this.searchMovie();
    }
}
</script>

<template>
<main>
    in
</main>
</template>

<style scoped></style>