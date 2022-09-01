<template>
  <div>
    <input type="text" placeholder="Search for a movie" v-model="myInput">
    <button @click="$emit('search', myInput)">SEARCH</button>
  </div>
</template>

<script>
export default {
    name: "MyHeader",
    data(){
        return {
            myInput: ''
        }
    }
}
</script>

<style scoped lang="scss">

</style>


