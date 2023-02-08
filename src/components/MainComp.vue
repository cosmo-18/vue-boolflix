<template>
  <div>
    <FilmList :arrayFilmFull="arrayFilmFull"/>
    <SerieList :arraySeriesFull="arraySeriesFull" />
  </div>
</template>

<script>
import FilmList from "./film/FilmList.vue";
import SerieList from "./tvseries/SerieList.vue";

export default {
  name: "MainComp",
  components: {
    FilmList,
    SerieList,
  },
  props:{
    //array with all the specific in App.vue
    arrayFilmFull: Array,
    arraySeriesFull: Array
  }
};
</script>

<style>
</style>