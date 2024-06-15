<script>
import { store } from '../store.js';
import StarsVote from './StarsVote.vue'
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

        getPosters(seriePoster) {
            let posterUrl = "http://image.tmdb.org/t/p/w342/" + seriePoster
            return posterUrl
        },

        toStarVote(vote) {
            let starsVote = Math.round(vote / 2)
            return starsVote
        }
    },
}

</script>

<template>
    <div class="wrapper">
        <ul v-for="(serie, index) in store.series">
            <li class="poster-container">
                <img v-if="serie.poster_path != null" :src="getPosters(serie.poster_path)" alt="">
                <div v-else class="movie-placeholder">
                    <p>{{ serie.name }}</p>
                </div>
            </li>
            <li>
                Titolo: {{ serie.name }}
            </li>
            <li>
                Titolo Originale: {{ serie.original_name }}
            </li>
            <li class="flex align-center">
                Lingua: <img :src="getFlag(serie.original_language.toUpperCase())" :alt="serie.original_language">
            </li>
            <li>
                <StarsVote :rating="serie.vote_average"/>
            </li>
        </ul>
    </div>
</template>

<style lang=scss scoped>
@use '../style/style-list.scss' as *;
</style>