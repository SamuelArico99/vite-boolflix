<script>
export default {
    name: 'AppCard',
    props: {
        element: Object
    },
    computed: {

        flag() {
            let lang = this.element.original_language;
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
    },
    methods: {
        getCover() {
            const baseCoverUrl = 'https://image.tmdb.org/t/p/';
            const coverSize = 'w342';
            const posterPath = this.element.poster_path;

            return baseCoverUrl + coverSize + posterPath;
        },
        getVote() {
            let newVote = this.element.vote_average;
            console.log('voto di partrnza: ', newVote)
            newVote = newVote / 2;
            console.log('voto / 2: ', newVote)
            newVote = Math.ceil(newVote);
            console.log('voto arrotondato: ', newVote)

            return newVote

        }
    }
}
</script>

<template>

    <div>

        <img :src="getCover()" alt="">
        <h3 v-if="element.title">
            {{ element.title }}
        </h3>
        <h3 v-else-if="element.name">
            {{ element.name }}
        </h3>
        <h4 v-if="element.original_title">
            {{ element.original_title }}
        </h4>
        <h4 v-else-if="element.original_name">
            {{ element.original_name }}
        </h4>
        <p>
            {{ element.original_language }}
        </p>
        <img :src="flag" alt="">
        <div>

            <span v-for="n in getVote()">★</span>
            <span v-for="n in (5 - getVote())">☆</span>
        </div>
    </div>

</template>

<style scoped>

</style>