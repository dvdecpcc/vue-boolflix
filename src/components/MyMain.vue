<template>
  <main>
    <ul class="myMovies">
        <li v-for="(movie, index) in movieList" :key="index">
            <img :src="'https://image.tmdb.org/t/p/w300' + movie.poster_path" alt="movie.title">
            {{movie.title}}
            {{movie.original_title}}
            <img class="flag" v-if="langFlags.includes(movie.original_language)" :src="require('../assets/flags/' + movie.original_language + '.png')" alt="">
            <span v-else>{{movie.original_language}}</span>
            {{movie.vote_average }}
        </li>    
    </ul>
    <ul class="mySeries">
        <li v-for="(serie, index) in seriesList" :key="index">
            <img :src="'https://image.tmdb.org/t/p/w300' + serie.poster_path" alt="serie.title">

            {{serie.name}}
            {{serie.original_name}}
            <img class="flag" v-if="langFlags.includes(serie.original_language)" :src="require('../assets/flags/' + serie.original_language + '.png')" alt="">
            <span v-else>{{serie.original_language}}</span>
            {{serie.vote_average }}
        </li>    
    </ul>
  </main>
</template>

<script>
export default {
    name: "MyMain",
    props: {
        movieList: Array,
        seriesList: Array
    },
    data(){
        return {
            langFlags: ['it', 'en', 'fr', 'de', 'nl', 'es', 'ja', 'ch', 'pt']
        }
    }
}
</script>

<style scoped lang="scss">
    .flag{max-width: 20px}
</style>