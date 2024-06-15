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


    },
}


</script>

<template>
    <header>
        <img src="https://ih1.redbubble.net/image.3350844638.4521/raf,360x360,075,t,fafafa:ca443f4786.jpg" alt="">
        <SearchBar class="search" @movieSearch="searchMovie" />
    </header>
</template>

<style lang="scss" scoped>
header {
    background-color: black;
    display: flex;
    height: 4rem;
    align-items: center;
    overflow: hidden;
    justify-content: space-between;
    padding: 0 2rem;
}

img {
    height: 7rem;
}
</style>