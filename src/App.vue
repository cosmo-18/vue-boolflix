<template>
  <div id="app">
    <HeaderComp @search="emitInputFilmName"/>
    <MainComp :arrayFilmFull="FilmsArray" :arraySeriesFull="SerieTvArray"/>  <!--Send the info to MainComp (child) -->
  </div>
</template>

<script>

import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'
import axios from 'axios'


export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data(){
    return{
      TextToSearch: '',
      FilmsArray: [],
      SerieTvArray: []
    }
  },
  mounted(){

  },
  methods:{
    emitInputFilmName(valoreEmit){
      this.TextToSearch = valoreEmit
      //call the function that search all the film spect
      this.getInfoFilm();
      this.getInfoSeries();
    },

    getInfoFilm(){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=c71ccc51695322240e536d0ad92b6f3c&language=en-US&page=1&include_adult=false&query=' + this.TextToSearch).then( (response) => {
        this.FilmsArray = response.data.results
      } )
    },

    getInfoSeries(){
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=c71ccc51695322240e536d0ad92b6f3c&language=en-US&page=1&include_adult=false&query=' + this.TextToSearch).then( (response) => {
        this.SerieTvArray=response.data.results
      } )
    }
  }
}
</script>

<style lang="scss">
*{
  font-family: Arial, Helvetica, sans-serif;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  box-sizing: border-box;
}

html,
#app{
  background-color: #141414;
}
</style>
