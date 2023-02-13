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
        <div>
            <h1>
                BOOFLIX
            </h1>
        </div>
        <div>
            <input type="text" v-model="store.searchText" placeholder="Inserisci il titolo di un film">
            <button @click="$emit('search')">
                Search
            </button>
        </div>
    </header>
</template>

<style scoped lang="scss">
header {
    width: 100%;
    height: 80px;
    background-color: black;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px;

    h1 {
        color: red;
    }

    input,
    button {

        height: 30px;
        border-radius: 10px;
        padding: 5px;
    }

    button {
        margin-left: 5px;
    }

}
</style>