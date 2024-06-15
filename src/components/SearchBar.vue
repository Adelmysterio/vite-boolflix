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
        <button @click="$emit('movieSearch', searched)"><font-awesome-icon icon="magnifying-glass" /></button>
        <input type="text" v-model="searched" @keyup.enter="$emit('movieSearch', searched)">
    </section>

</template>

<style lang="scss" scoped>
section {
    display: flex;
    width: 25%;

    button {
        background-color: transparent;
        color: white;
        border: none;
        font-size: 1.5rem;
        margin-right: 1rem;
        cursor: pointer;
    }

    input {
        width: 100%;
        background-color: transparent;
        border: 2px solid white;
        border-radius: 10px;
        color: white;
        font-size: 1rem;
        padding: .4rem 1rem;
    }
}
</style>
