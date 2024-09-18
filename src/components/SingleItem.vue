<script>
import axios from 'axios';

export default {
  props:{
    title: String,
    originalTitle: String,
    language: String,
    vote: Number
  },
  methods: {
    getFlag(lang){
      const validLangs = [
        'en',
        'it',
        'ja'
      ];

      if(validLangs.includes(lang)){
        if (lang == 'ja') {
          return '/img/flags/jp.gif';
        }
        else{
          return '/img/flags/' + lang + '.gif';
        }
      }
      else{
        return '';
      }
    }
  }

}
</script>

<template>
    <section>
      <ul class="p-4 border">
        <li>
          Titolo: {{ title }}
        </li>
        <li>
          Titolo originale: {{ originalTitle }}
        </li>
        <li>
          Lingua: <img :src="getFlag(language)" alt="">
        </li>
        <li>
          Voto: {{ vote }}
        </li>
      </ul>
    </section>
</template>

<style lang="scss" scoped>
</style>