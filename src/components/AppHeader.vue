<script>
import { store } from '../store';

export default {
    name: ' AppHeader',
    data() {
        return {
            store
        };
    },
    components: {

    },
    methods: {

    }
};
</script>

<template>
    <header>
        <input type="text" v-model="store.searchText" placeholder="inserisci titolo film">
        <button @click="$emit('search')">
            Search
        </button>
    </header>
</template>

<style scoped>

</style>