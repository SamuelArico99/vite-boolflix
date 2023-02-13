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

    <div class="element-card">

        <div class="front">
            <img :src="getCover()" alt="">
        </div>
        <div class="back">
            <h3 v-if="element.title">
                {{ element.title }}
            </h3>
            <h3 v-else-if="element.name">
                {{ element.name }}
            </h3>
            <h4 v-if="element.original_title">
                Titolo originale: {{ element.original_title }}
            </h4>
            <h4 v-else-if="element.original_name">
                {{ element.original_name }}
            </h4>
            <p>
                Lingua originale: {{ element.original_language }}
            </p>
            <img :src="flag" alt="">
            <div>

                <span v-for="n in getVote()">★</span>
                <span v-for="n in (5 - getVote())">☆</span>
            </div>
            <p>
                {{ element.overview }}
            </p>
        </div>
    </div>

</template>

<style scoped lang="scss">
.element-card {
    position: relative;
    width: 20%;

    .front,
    .back {
        width: 100%;
        height: 100%;
    }

    .back {
        width: 100%;
        height: 100%;
        display: none;
        position: absolute;
        top: 0;
        left: 0;
        color: white;
        text-align: center;
        padding: 30px;
        overflow-x: hidden;
        overflow-y: auto;

        h3,
        h4,
        div,
        p {
            margin: 30px 0;
        }
    }

    .front {
        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }

    .back {
        display: none;
    }

    &:hover {
        .back {
            display: block;
            background-color: rgba(0, 0, 0, 0.7);
        }
    }
}
</style>