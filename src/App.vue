<template>
  <div id="app">
    
   <search @SearchRequested="handleSearch"></search>
   <p v-if="isLoadig">Loading..</p>
   <preview :gifs=gifs></preview>
  </div>
</template>

<script>
import Search from './components/Search.vue'
import Preview from './components/Preview.vue'
export default {
  name: 'app',
  components:{Search, Preview},
  data(){
    return {
      isLoadig:true,
      gifs:[]
    }
  },
  methods:{
    handleSearch(query){
      this.gifs=[];
      this.isLoadig=true;
      fetch(`//api.giphy.com/v1/gifs/search?q=${query}&api_key=dc6zaTOxFJmzC `)
      .then((res)=> {return res.json()})
      .then((res)=> {
      this.gifs=res.data;
      this.isLoadig=false;})

    }
  },
  created(){
    fetch('//api.giphy.com/v1/gifs/trending?api_key=dc6zaTOxFJmzC')
    .then((res)=> {return res.json()})
    .then((res)=> {
      this.gifs=res.data;
      this.isLoadig=false;})
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

}


</style>
