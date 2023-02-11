<script>
import { store } from "../store";
import AppCard from "./AppCard.vue";
export default {
    name: ' AppMain',
    data() {
        return {
            store
        };
    },
    components: {
        AppCard
    },
    methods: {

    }
};
</script>

<template>
    <main>
        <h1>Film</h1>

        <AppCard v-for="movie in store.movies" :element=movie />

        <h1>Serie tv</h1>

        <AppCard v-for="serie in store.series" :element=serie />
    </main>
</template>

<style scoped>

</style>