<template>
  <main>
    <ul class="myMovies">
        <li v-for="(movie, index) in movieList" :key="index">
            <img :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path" alt="movie.title">
            TITOLO:{{movie.title}}
            TITOLO ORIGINALE:{{movie.original_title}}
            <img class="flag" v-if="langFlags.includes(movie.original_language)" :src="require('../assets/flags/' + movie.original_language + '.png')" alt="">
            <span v-else>{{movie.original_language}}</span>
            <div>
                VOTO:<i v-for="x in 5" class="fa-star" :class="(x>myVote(movie.vote_average))?'fa-regular':'fa-solid'" :key="x"></i>
            </div>
        </li>    
    </ul>
    <ul class="mySeries">
        <li v-for="(serie, index) in seriesList" :key="index">
            <img :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path" alt="serie.title">

            TITOLO:{{serie.name}}
            TITOLO ORIGINALE:{{serie.original_name}}
            <img class="flag" v-if="langFlags.includes(serie.original_language)" :src="require('../assets/flags/' + serie.original_language + '.png')" alt="">
            <span v-else>{{serie.original_language}}</span>
             <div>
                VOTO:<i v-for="x in 5" class="fa-star" :class="(x>myVote(serie.vote_average))?'fa-regular':'fa-solid'" :key="x"></i>
            </div>
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
    },
    methods: {
        myVote(starredVote){
            return Math.ceil(starredVote / 2);
        }
    }
}
</script>

<style scoped lang="scss">
    main{
        background-color: rgb(42, 51, 53);
        color: white;
        height: 100vh;
    }
    .flag{max-width: 50px;}
</style>