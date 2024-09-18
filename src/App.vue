<script>
/* 
Per importare ed utilizzare un componente dentro ad un altro devo SEMPRE seguire 3 passi:
1. Importazione del componente
2. Dichiarazione del componente
3. Utilizzo del componente
*/

//1. Importazione del componente
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store.js'
import axios from 'axios';

export default {
  data(){
    return{
      store,
      apiKey: 'f33dda6a8c7921fc881453a17c83a9d8',
    };
  },
  // 2. Dichiarazione del componente
  components: {
    AppHeader,
    AppMain
  },
  methods: {
    search(){
      console.log(this.store.searchText);

        axios
          .get('https://api.themoviedb.org/3/search/movie', {
            params: {
              api_key: this.apiKey,
              query: this.store.searchText,
            }
          })
          .then((resp) => {
            console.log('MOVIE', resp.data);
            this.store.movies = resp.data.results;
          });

          axios
          .get('https://api.themoviedb.org/3/search/tv', {
            params: {
              api_key: this.apiKey,
              query: this.store.searchText,
            }
          })
          .then((resp) => {
            console.log('SERIES', resp.data);
            this.store.series = resp.data.results;
          });
    }
  },
  beforeCreate(){
    console.log('Before Create');
  },
  created(){
    console.log('Created');
  }
}
</script>

<template>
  <!--3. Utilizzo del componente-->
  <AppHeader @search="search()" />
  <AppMain />
</template>

<style lang="scss">
@use 'assets/scss/main.scss' as *;
@import 'bootstrap/scss/bootstrap';
</style>
