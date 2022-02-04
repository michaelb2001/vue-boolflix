<template>
  <div id="app">
    <Header 
    @chiama2="ricerca" />
    <Main 
    :lista="mioArray"/>  
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
        arrayFilm:[],
        arraySerie: [],
        apiURLFilm : "https://api.themoviedb.org/3/search/movie",
        apiURLSerie: "https://api.themoviedb.org/3/search/tv",

        image : ""
    }
  },
  created: function () {
      this.ricerca();
  },
  methods:{
      getFilms : function(){
        console.log("dentro getfilms")
        axios.get(this.apiURLFilm, {
          params: {
            api_key: "6a51bfbc3fd574de9c1f2701377490e6",
            language : "it-IT",
            query : this.nomeRicerca       
          }
        })
        .then((risposta)=> {
          this.arrayFilm = risposta.data.results;
          return this.arrayFilm;
        })
        .catch((error)=> {
          console.log(error);
        })
        .then(function () {
          // always executed
        });  
    },
    getSerie: function(){
        axios.get(this.apiURLSerie, {
          params: {
            api_key: "6a51bfbc3fd574de9c1f2701377490e6",
            language : "it-IT",
            query : this.nomeRicerca       
          }
        })
        .then((risposta)=> {
            this.arraySerie = risposta.data.results;
            return this.arraySerie;
        })
        .catch((error)=> {
          console.log(error);
        })
        .then(function () {
          // always executed
        });  
    },
  
    ricerca: function(valore){
      this.nomeRicerca = valore;
      this.getFilms();
      this.getSerie();
      /*this.mioArray.concat(this.getFilms());
      this.mioArray.concat(this.getSerie());*/

    },
  },
      computed:{
        mioArray: function(){
          let arrayApp = [];
          arrayApp = [...this.arrayFilm,...this.arraySerie];
          console.log(arrayApp);
          return arrayApp;
        }
    }
}
</script>

<style lang="scss">

@import './assets/global.scss';
</style>
