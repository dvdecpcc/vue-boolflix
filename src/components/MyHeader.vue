<template>
  <div>
    <h1>BOOLFLIX</h1>
    <div>
        <input type="text" placeholder="Search for a movie" v-model="myInput">
        <button @click="$emit('search', myInput)">SEARCH</button>
    </div>
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
    div{
        height: 60px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        background-color: rgb(0, 0, 0);

        h1{
            color: rgb(212, 0, 0);
            font-size: 2rem;
            padding: 10px;
        }
        button{
            background-color: rgb(10, 10, 10);
            color: white;
            border: .5px solid white;
            margin: 0 10px;
            padding: 0 5px;
        }
        input{
            font-size: .8rem;
            padding: 0 5px;
        }
    }
</style>


