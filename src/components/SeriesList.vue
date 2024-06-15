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
        <article v-for="(serie, index) in store.series">
            <figure class="poster-container" :style="{ backgroundImage: `url(${getPosters(serie.poster_path)})`}">
                <h3 v-show="serie.poster_path == null">{{ serie.name }}</h3>
                <ul>
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
                        <StarsVote :rating="serie.vote_average" />
                    </li>
                    <li>
                        Overview: {{ serie.overview }}
                    </li>
                </ul>
            </figure>
        </article>
    </div>
</template>

<style lang=scss scoped>
@use '../style/style-list.scss' as *;
</style>