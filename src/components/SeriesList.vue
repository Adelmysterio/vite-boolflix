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
</template>

<style lang=scss scoped></style>