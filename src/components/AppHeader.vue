<script>
import axios from 'axios';
import SingleItem from './SingleItem.vue';

export default {
  
  data() {
    return {
      apiKey: 'f33dda6a8c7921fc881453a17c83a9d8',
      searchText: '',
      movies: [],
      series: [],
    }
  },
  components: { 
    SingleItem 
  },
  methods: {
    search(){
      console.log(this.searchText);

        axios
          .get('https://api.themoviedb.org/3/search/movie', {
            params: {
              api_key: this.apiKey,
              query: this.searchText,
            }
          })
          .then((resp) => {
            console.log('MOVIE', resp.data);
            this.movies = resp.data.results;
          });

          axios
          .get('https://api.themoviedb.org/3/search/tv', {
            params: {
              api_key: this.apiKey,
              query: this.searchText,
            }
          })
          .then((resp) => {
            console.log('SERIES', resp.data);
            this.series = resp.data.results;
          });
    }
  }

}
</script>

<template>
    <header>
      <div class="container">
        <div id="navbar" class="d-flex">
          <input v-model="searchText" type="text" placeholder="Cerca film o serie TV..">
          <button @click="search">
            Cerca
          </button>
        </div>
      
        <!--MOVIES-->
        <div>
          <h3>MOVIES</h3>
          <ol>
            <li v-for="(movie, i) in movies" :key="i">

              <SingleItem 
                :title="movie.title"
                :originalTitle="movie.original_title"
                :language="movie.original_language"
                :vote="movie.vote_average"
              />

              <hr>
              
            </li>
          </ol>
        </div>

        <hr>

        <!--SERIES-->
        <div>
          <h3>SERIES</h3>

          <ol>
            <li v-for="(serie, i) in series" :key="i">

              <SingleItem 
                :title="serie.name"
                :originalTitle="serie.original_name"
                :language="serie.original_language"
                :vote="serie.vote_average"
              />
              
              <hr>

            </li>
          </ol>
        </div>
      </div>
    </header>
</template>

<style scoped>
header{
  padding: 20px 0;
}

#navbar{
  margin-bottom: 20px;
}
</style>