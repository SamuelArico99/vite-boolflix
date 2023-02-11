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
    }
}
</script>

<template>

    <div>
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
        <p>
            {{ element.vote_average }}
        </p>
    </div>

</template>

<style scoped>

</style>