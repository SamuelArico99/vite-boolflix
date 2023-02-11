<script>
export default {
    name: 'AppCard',
    props: {
        movie: Object
    },
    computed: {

        flag() {
            let lang = this.movie.original_language;
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
}
</script>

<template>

    <div>
        <h2>
            {{ movie.title }}
        </h2>
        <h4>
            {{ movie.original_title }}
        </h4>
        <p>
            {{ movie.original_language }}
        </p>
        <img :src="flag" alt="">
        <p>
            {{ movie.vote_average }}
        </p>
    </div>

</template>

<style scoped>

</style>