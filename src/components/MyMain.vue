<template>
  <div>
    <ul>
        <li v-for="(movie, index) in movieList" :key="index">
            {{movie.title}}
            {{movie.original_title}}
            <img v-if="langFlags.includes(movie.original_language)" :src="require('../assets/flags/' + movie.original_language + '.png')" alt="">
            <span v-else>{{movie.original_language}}</span>
            {{movie.vote_average }}
        </li>    
    </ul>
  </div>
</template>

<script>
export default {
    name: "MyMain",
    props: {
        movieList: Array
    },
    data(){
        return {
            langFlags: ['it', 'en', 'fr', 'de', 'nl', 'es', 'jp', 'ch', 'por']
        }
    }
}
</script>

<style scoped lang="scss">

</style>