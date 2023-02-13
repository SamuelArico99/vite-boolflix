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
        <div class="cards-container">
            <AppCard v-for="movie in store.movies" :element=movie />
        </div>

        <h1>Serie tv</h1>

        <div class="cards-container">
            <AppCard v-for="serie in store.series" :element=serie />
        </div>
    </main>
</template>

<style scoped lang="scss">
.cards-container {
    display: flex;
    flex-wrap: wrap;
}

h1 {
    color: white;
}

main {
    background-color: #2b2626;
}
</style>