<template>
  <div>
    <ul>
        <li v-for="(movie, index) in movieList" :key="index"></li>
            
            {{movie.original_title}}
            {{movie.original_language}}
            {{movie.vote_average }}
    </ul>
  </div>
</template>

<script>
export default {
    name: "MyMain",
    props: {
        movieList: Array
    }
}
</script>

<style>

</style>