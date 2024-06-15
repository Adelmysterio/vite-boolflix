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
        <h1 v-if="store.movies.length > 0">Film</h1>
        <MovieList />
        <h1 v-if="store.series.length > 0">Serie TV</h1>
        <SeriesList />
    </main>
</template>

<style lang="scss" scoped>
@use '../style/partials/variables' as *;

main {
    background-color: $gray;
    width: 100%;
    height: 100vh;
    overflow: scroll;
    padding: 5rem 2rem;
    color: white;
}

h1 {
    margin-bottom: 1rem;
}
</style>