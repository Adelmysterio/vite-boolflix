<script>
import axios from 'axios';

export default {
    data() {
        return {
            actors: [],
        }
    },
    props: {
        id: Number
    },
    methods: {
        getActors(num) {
            axios.get(`https://api.themoviedb.org/3/movie/${num}/credits`, {
                params: {
                    api_key: 'e99307154c6dfb0b4750f6603256716d',
                }
            })
                .then((response) => {
                    console.log(response.data.cast.slice(0, 5).map(item => item.name))
                    this.actors = response.data.cast.slice(0, 5).map(item => item.name);
                })
                .catch((error) => {
                    console.error(error);
                });
        },
    },
    mounted() {
        this.getActors(this.id);
    },
}
</script>

<template>
    <div>
        <ul>Actors:
            <li v-for="(actor, index) in actors" :key="index">
                {{ actor }}
            </li>
        </ul>
    </div>
</template>

<style lang="scss" scoped>
div {

    margin-bottom: .7rem;
}
ul {
    display: inline;
    margin-right: 1rem;

    li {
        display: inline;
        margin-right: .7rem;
    }
}
</style>