<template>
  <main>
    <ul class="myMovies">
        <li class="myCard" v-for="(movie, index) in movieList" :key="index">
            <div class="frontCard">
                <img :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path" alt="movie.title">
            </div>
            <div class="backCard">
                <p>TITOLO:{{movie.title}}</p> 
                <p>TITOLO ORIGINALE:{{movie.original_title}}</p> 
                <img class="flag" v-if="langFlags.includes(movie.original_language)" :src="require('../assets/flags/' + movie.original_language + '.png')" alt="">
                <p v-else>{{movie.original_language}}</p>
                <div>
                   <p>VOTO:<i v-for="x in 5" class="fa-star" :class="(x>myVote(movie.vote_average))?'fa-regular':'fa-solid'" :key="x"></i></p> 
                </div>
            </div>
            
        </li>    
    </ul>
    <ul class="mySeries">
        <li class="myCard" v-for="(serie, index) in seriesList" :key="index">
            <div class="frontCard">
                <img :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path" alt="serie.title">
            </div>
            <div class="backCard">
                <p>TITOLO:{{serie.name}}</p>
                <p>TITOLO ORIGINALE:{{serie.original_name}}</p> 
                <img class="flag" v-if="langFlags.includes(serie.original_language)" :src="require('../assets/flags/' + serie.original_language + '.png')" alt="">
                <p v-else>{{serie.original_language}}</p>
                <div>
                   <p>VOTO:<i v-for="x in 5" class="fa-star" :class="(x>myVote(serie.vote_average))?'fa-regular':'fa-solid'" :key="x"></i></p>
                </div>
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
        li{
            list-style: none;
        }


        .mySeries, .myMovies{
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
        }

        .myCard{
            width: calc(100% / 3);
            margin: 50px;

            .frontCard img{
                object-fit: cover;
                width: 100%;
            }
            .backCard{
                display: none;
                background-color: black;
                color: white;
            }
            .backCard:hover{
                display: block;
                transform: rotateY(180deg);
            }
        }
        .flag{max-width: 50px;}

    }
    
</style>