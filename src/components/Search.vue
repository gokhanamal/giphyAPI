<template>
    <div class="search">
        <input type="text" v-model="query" @keypress.enter="handleSearch"/>
        <button @click="handleSearch">Search</button>     
    </div>
</template>

<script>
    export default {
        data (){
            return {
                query:''
            }
        },
        methods:{
            handleSearch() {
                this.$emit('SearchRequested',this.query);
            }
        }
    }
</script>

<style>
  .search input {
      padding: 10px 20px;
      border: 1px solid #ccc;
      border-radius: 5px;
      width: 400px;
  }
  .search button {
        width: 75px;
        height: 38px;
        border-radius: 5px;
        border:1px solid #ccc;
        font-size: 15px;
        color: white;
        background-color: #2866AB;

  }

  .search button:hover {
      filter: brightness(120%);
  }
  .search {
      text-align: center;
  }
</style>