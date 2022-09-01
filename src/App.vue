<template>
  <div id="app">
    <MyHeader @search="searching"/>
    <MyMain :movieList="movieList" :seriesList="seriesList"/>
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
      movieList: [],
      seriesList: []
    }
  },
  methods: {
    searching(research){
      const parameters = {
        params: {
        api_key: this.apiKey,
        language: this.language,
        query: research
        } 
      };
      this.getMovies(parameters);
      this.getSeries(parameters);
    },
    getMovies(parameters) {
      axios.get(this.apiUrl + '/search/movie', parameters)
      .then(res =>{
        this.movieList = res.data.results;
      })
    },
     getSeries(parameters) {
      axios.get(this.apiUrl + '/search/tv', parameters)
      .then(res =>{
        this.seriesList = res.data.results;
      })
    }
  }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.css';

</style>
