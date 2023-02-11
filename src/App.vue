<script >
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from "./store";


export default {
  name: ' App',
  data() {
    return {
      store
    }
  },
  components: {
    AppHeader,
    AppMain
  },
  methods: {
    searchEvent() {
      this.search('movie');
      this.search('tv');
    },
    search(type) {

      let url = 'https://api.themoviedb.org/3/search/';
      console.log(this.store.searchText);

      axios
        .get(url + type, {
          params: {
            api_key: 'e99307154c6dfb0b4750f6603256716d',
            query: this.store.searchText,
            language: 'it-IT'
          }

        })
        .then((response) => {
          if (type == 'movie') {
            this.store.movies = response.data.results;
          }
          else {
            this.store.series = response.data.results;
          }

        });
    }
  }
};
</script>

<template>

  <AppHeader @search="searchEvent" />

  <AppMain />

</template>

<style scoped>

</style>
