<script>
import { store } from '../store.js';
export default {
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
        }
    },
}
</script>

<template>
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
</template>

<style lang=scss scoped>
</style>