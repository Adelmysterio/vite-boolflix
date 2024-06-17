<script>
import axios from 'axios';

export default {
    data() {
        return {
            tvActors: []
        }
    },
    props: {
        id: Number
    },
    methods: {
        getTvActors(num) {
            axios.get(`https://api.themoviedb.org/3/tv/${num}/credits`, {
                params: {
                    api_key: 'e99307154c6dfb0b4750f6603256716d',
                }
            })
                .then((response) => {
                    console.log(response.data.cast.slice(0, 5).map(item => item.name))
                    this.tvActors = response.data.cast.slice(0, 5).map(item => item.name);
                })
                .catch((error) => {
                    console.error(error);
                });
        },
    },
    mounted() {
        this.getTvActors(this.id)
    },
}
</script>

<template>
    <div>
        <ul>Actors:
            <li v-for="(actor, index) in tvActors" :key="index">
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