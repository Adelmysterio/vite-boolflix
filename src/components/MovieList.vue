<script>
import StarsVote from './StarsVote.vue'
import { store } from '../store.js';
export default {

    components: {
        StarsVote
    },

    data() {
        return {
            store,
        }
    },

    methods: {
        getFlag(nation) {
            let flag = "https://flagsapi.com/" + nation + "/flat/16.png"
            if (nation == "EN") {
                flag = "https://flagsapi.com/GB/flat/16.png"
            }
            return flag
        },

        getPosters(moviePoster) {
            let posterUrl = "http://image.tmdb.org/t/p/w342/" + moviePoster
            return posterUrl
        },

    },
}
</script>

<template>
    <div class="wrapper">
        <article v-for="(movie, index) in store.movies">
            <figure class="poster-container">
                <img v-if="movie.poster_path != null" :src="getPosters(movie.poster_path)"
                    :alt="movie.title + ' Poster Images'">
                <div v-else class="movie-placeholder">
                    <p>{{ movie.title }}</p>
                </div>
            </figure>
            <ul>
                <li>
                    Titolo: {{ movie.title }}
                </li>
                <li>
                    Titolo Originale: {{ movie.original_title }}
                </li>
                <li class="flex align-center">
                    Lingua: <img :src="getFlag(movie.original_language.toUpperCase())" :alt="movie.original_language">
                </li>
                <li>
                    <StarsVote :rating="movie.vote_average" />
                </li>
            </ul>
        </article>
    </div>
</template>

<style lang=scss scoped>
@use '../style/style-list.scss' as *;
</style>