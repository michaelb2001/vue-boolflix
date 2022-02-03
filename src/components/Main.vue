<template>
  <div class="container-fluid d-flex flex-wrap align-items-center justify-content-center">
      <ul>
        <li v-for="(element,index) in listaFilms" :key="index">
            {{element.title}} , {{element.original_title}} ,
            <img v-if="element.original_language == 'en' " src="../assets/img/en.png">
            <img v-else-if="element.original_language == 'it' " src="../assets/img/it.png"> 
            <img v-else-if="element.original_language == 'de' " src="../assets/img/de.png">  
            <img v-else src="../assets/img/peace.jpg"> , 
            {{element.vote_average}}

        </li>
      </ul>
  </div>
</template>

<script>
export default {
    name:"Main",
    props:{
        listaFilms :Array
    },
    data(){
        return {
            lingua : ""
        }
    },
    methods:{
        immagineLinguaOriginale: function(){
           if( this.listaFilms.original_language == "en"){
               this.lingua="../assets/img/en.png";
               return this.lingua;
           }
        }  
        }
}
</script>

<style lang="scss" scoped>
@import '../assets/vars.scss';
.container-fluid{
    min-height: 100vh;
    background-color: $third-color;

    ul{
        list-style-type: none;

        li{
            color: $second-color;
            text-decoration: none;
            margin: 20px 0px;

            img{
                width: 18px;
                height: 18px;
            }
        }
    }
}
</style>