<script>
import axios from 'axios';
import {store} from '../store.js'

export default {
  
  data() {
    return {
      store,
    };
  }
}
</script>

<template>
    <header>
      <div class="container">
        <div id="navbar" class="d-flex">
          <input v-model="store.searchText" type="text" placeholder="Cerca film o serie TV..">
          <button @click="$emit('search')">
            Cerca
          </button>
        </div>
      </div>
    </header>
</template>

<style lang="scss" scoped>
header{
  padding: 20px 0;
}

#navbar{
  margin-bottom: 20px;
}
</style>