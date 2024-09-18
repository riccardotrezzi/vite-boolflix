<script>
import axios from 'axios';

export default {
  data() {
    return {
      apiKey: 'f33dda6a8c7921fc881453a17c83a9d8',
      searchText: '',
      movies: []

    }
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
              console.log(resp.data);
              this.movies = resp.data.results;
            });
      }
  }

}
</script>

<template>
    <header>
      <div class="container">
        <div class="d-flex">
          <input v-model="searchText" type="text" placeholder="Cerca film o serie TV..">
          <button @click="search">
            Cerca
          </button>
        </div>
      

        <div>
          <ol>
            <li v-for="(movie, i) in movies" :key="i">
              <ul>
                <li>
                  Titolo: {{movie.title}}
                </li>
                <li>
                  Titolo originale: {{movie.original_title}}
                </li>
                <li>
                  Lingua: {{movie.original_language}}
                </li>
                <li>
                  Voto: {{movie.vote_average}}
                </li>
              </ul>
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

</style>