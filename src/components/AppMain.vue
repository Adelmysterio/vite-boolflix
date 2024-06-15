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
        <div class="container">
            <h1 v-if="store.movies.length > 0">Film</h1>
            <MovieList />
            <h1 v-if="store.series.length > 0">Serie TV</h1>
            <SeriesList />
        </div>
    </main>
</template>

<style lang="scss" scoped>
@use '../style/partials/variables' as *;

main {
    background-color: $gray;
    width: 100%;
    height: calc(100vh - 4rem);
    overflow-y: scroll;
    color: white;
padding: 2rem;
}

h1 {
    margin-bottom: 1rem;
}
</style>