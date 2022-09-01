<template>
  <div>
    <ul>
        <li v-for="(movie, index) in movieList" :key="index">
            {{movie.title}}
            {{movie.original_title}}
            {{movie.original_language}}
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
    }
}
</script>

<style scoped lang="scss">

</style>