<template>
  <div id="app">
    <MyHeader @search="searching"/>
    <MyMain :movieList="movieList"/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import MyMain from './components/MyMain.vue';
import axios from 'axios';


export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
  },
  data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3',
      apiKey: 'a3ed888e36325b73e39c2587ed60534a',
      language: 'it-IT',
      movieList: []
    }
  },
  methods: {
    searching(research){
      axios.get(this.apiUrl + '/search/movie?api_key=' + this.apiKey + '&language=' + this.language + '&query=' + research)
      .then(res =>{
        this.movieList = res.data.results;
      })
    }
  }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.css';

</style>
