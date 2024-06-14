<script>
import { store } from '../store.js';
export default {
    data() {
        return {
            store,
            searched: ''
        }
    }
}
</script>

<template>
    <section>
        <input type="text" v-model="searched" @keyup.enter="$emit('movieSearch', searched)">
        <button @click="$emit('movieSearch', searched)">Search</button>
    </section>

</template>

<style lang="scss" scoped>
input {
    margin-bottom: 2rem;
}
</style>
