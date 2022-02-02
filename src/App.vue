<template>
  <div id="app">
    <Header />
  </div>
</template>

<script>
import Header from './components/Header.vue';

export default {
  name: 'App',
  components: {
    Header
  },
  data(){
    return{
        apiURL : "https://api.themoviedb.org/3/movie/550?api_key=6a51bfbc3fd574de9c1f2701377490e6",
        
    }
  }
}
</script>

<style lang="scss">

@import './assets/global.scss';
</style>
