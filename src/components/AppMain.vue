<script >
import { store } from "../store";
export default {
    name: ' AppMain',
    data() {
        return {
            store
        };
    },
    components: {

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
        <h2>Film</h2>
        <div v-for="movie in store.movies">
            <h2>
                {{ movie.title }}
            </h2>
            <h4>
                {{ movie.original_title }}
            </h4>
            <p>
                {{ movie.original_language }}
            </p>
            <img :src="flag(movie.original_language)" alt="">
            <p>
                {{ movie.voto_average }}
            </p>
        </div>

        <h2>Serie tv</h2>
        <div v-for="serie in store.series">
            <h2>
                {{ serie.name }}
            </h2>
            <h4>
                {{ serie.original_name }}
            </h4>
            <p>
                {{ serie.original_language }}
            </p>
            <img :src="flag(serie.original_language)" alt="">
            <p>
                {{ serie.voto_average }}
            </p>
        </div>
    </main>
</template>

<style scoped>

</style>