<script>
/* 
Per importare ed utilizzare un componente dentro ad un altro devo SEMPRE seguire 3 passi:
1. Importazione del componente
2. Dichiarazione del componente
3. Utilizzo del componente
*/

//1. Importazione del componente
import AppFooter from './components/AppFooter.vue';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';

export default {
  data() {
    return { 
      message: ''
    }
  },
  // 2. Dichiarazione del componente
  components: {
    AppHeader,
    AppMain,
    AppFooter
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
  <AppHeader />
  <AppMain />
  <AppFooter />
</template>

<style lang="scss">
@use 'assets/scss/main.scss' as *;
@import 'bootstrap/scss/bootstrap';
</style>
