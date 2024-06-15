<script>
import { store } from '../store.js';
import MovieList from './MovieList.vue';
import SeriesList from './SeriesList.vue';

export default {
    components: {
        MovieList,
        SeriesList
    },

    data() {
        return {
            store,
        }
    },

}
</script>

<template>
    <main>
        <h1>Film</h1>
        <MovieList />
        <h1>Serie TV</h1>
        <SeriesList />
    </main>
</template>

<style lang="scss" scoped>

h1 {
    margin-bottom: 1rem;
}

</style>