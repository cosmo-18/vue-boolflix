<template>
  <div class="header">
    <img src="./Logonetflix.png" alt="logo">
    <div class="align-self-center">
      <input type="text" v-model="textToSearch" placeholder="Insert a title" @keyup.enter="sendTextFilm">
    </div>
  </div>
</template>

<script>
export default {
    name: 'HeaderComp',
    components:{

    },
    data(){
      return{
        textToSearch: 'p',
      }
    },
    mounted(){
      this.sendTextFilm();
    },
    methods:{
      sendTextFilm(){
        this.$emit('search', this.textToSearch)
      }
    }
}
</script>

<style scoped>
.header{
  display: flex;
  justify-content: space-between;
  height: 5rem;
  padding: 20px;
}
</style>