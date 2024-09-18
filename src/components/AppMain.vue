<script>
import axios from 'axios';
import { store } from '../store.js'
import SingleItem from './SingleItem.vue';

export default {
  
  data() {
    return {
      store,
    };
  },
  components: { 
    SingleItem 
  }
}
</script>

<template>
    <main>
      <div class="container">

        <!--MOVIES-->
        <div>
          <h3>MOVIES</h3>
          <ol>
            <li v-for="(movie, i) in store.movies" :key="i">

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
            <li v-for="(serie, i) in store.series" :key="i">

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
    </main>
</template>

<style scoped>
main{
  padding: 20px 0;
}
</style>