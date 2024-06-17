<script>
import StarsVote from './StarsVote.vue'
import ActorsList from './ActorsList.vue';
import { store } from '../store.js';
export default {

    components: {
        StarsVote,
        ActorsList
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
            <figure class="poster-container" :style="{ backgroundImage: `url(${getPosters(movie.poster_path)})` }">
                <h3 v-show="movie.poster_path == null">{{ movie.title }}</h3>
                <ul>
                    <li>
                        Titolo: {{ movie.title }}
                    </li>
                    <li>
                        Titolo Originale: {{ movie.original_title }}
                    </li>
                    <li>
                        <ActorsList :id="movie.id"/>
                    </li>
                    <li class="flex align-center">
                        Lingua: <img :src="getFlag(movie.original_language.toUpperCase())"
                            :alt="movie.original_language">
                    </li>
                    <li>
                        <StarsVote :rating="movie.vote_average" />
                    </li>
                    <li>
                        Overview: {{ movie.overview }}
                    </li>
                </ul>
            </figure>
        </article>
    </div>
</template>

<style lang=scss scoped>
@use '../style/style-list.scss' as *;
</style>