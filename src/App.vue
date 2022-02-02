<template>
  <div id="app">
    <Header 
    @chiama2="ricerca" />
    <Main 
    :listaFilms="mioArray"/>  
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
        nomeRicerca :"",
        mioArray : [],
        apiURL : "https://api.themoviedb.org/3/search/movie"
    }
  },
  created: function () {
      this.getFilms();
  },
  methods:{
      getFilms : function(){
        axios.get(this.apiURL, {
          params: {
            api_key: "6a51bfbc3fd574de9c1f2701377490e6",
            language : "it-IT",
            query : this.nomeRicerca       
          }
        })
        .then((risposta)=> {
          this.mioArray = risposta.data.results;
          console.log(this.mioArray);
        })
        .catch((error)=> {
          console.log(error);
        })
        .then(function () {
          // always executed
        });  
    },
    ricerca: function(valore){
      console.log(valore);
        this.nomeRicerca = valore;
        this.getFilms();
    }
  }
}
</script>

<style lang="scss">

@import './assets/global.scss';
</style>
