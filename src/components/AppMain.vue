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
        flag(lang) {
            if (lang == 'en') {
                lang = 'uk'
            }
            else if (lang == 'pt') {
                lang = 'po'
            }
            else if (lang == 'es') {
                lang = 'sp'
            }
            const flag = ` https://www.worldometers.info//img/flags/small/tn_${lang}-flag.gif`;
            return flag;
        }
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