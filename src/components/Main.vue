<template>
  <div class="container-fluid d-flex flex-wrap align-items-start justify-content-center">
      <ul v-for="(element,index) in lista" :key="index" 
      class="d-flex flex-column justify-content-center align-items-center text-center">
        <li>
            <div>
                <img v-if="element.poster_path != null" class="poster" :src="apiIMG+element.poster_path" alt="">
            </div>
        </li>
        <div class="nullo d-flex justify-content-center align-items-center text-center border border-danger" v-if="element.poster_path == null ">
            <h1>{{element.title}} {{element.name}}</h1>
        </div>
        <li> Titolo : {{element.title}} {{element.name}}</li>
        <li> Titolo Originale : {{element.original_title}} {{element.original_name}} </li>
        <li> Lignua Originale : <img v-if="element.original_language == 'en' " src="../assets/img/en.png">
            <img v-else-if="element.original_language == 'it' " src="../assets/img/it.png"> 
            <img v-else-if="element.original_language == 'de' " src="../assets/img/de.png">  
            <img v-else src="../assets/img/peace.jpg">
        </li>
        <li class="d-flex">
            Voto :&nbsp;
            <div class="d-flex align-items-center">
                <div v-for="(elemento,indice) in stelline(element.vote_average)" :key="indice">
                    <i class="fas fa-star piene"></i>
                </div>

                <div  v-for="(elemento,indice) in (5 - stelline(element.vote_average))" :key="indice"> 
                    <i class="fas fa-star vuote"></i>
                </div>
            </div>
        </li>        
      </ul>

  </div>
</template>

<script>
export default {
    name:"Main",
    props:{
        lista : Array
    },
    data(){
        return {
            lingua : "",
            apiIMG : "https://image.tmdb.org/t/p/w300"
        }
    },
    methods:{
        stelline: function(voto){
            return Math.ceil( voto / 2 );
        }   
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/vars.scss';
.container-fluid{
    position: relative;
    min-height: 100vh;
    background-color: $third-color;

    ul{
        position: relative;
        list-style-type: none;
        border-radius: 5px;
        padding: 5px;
        margin:20px;
        min-width: 300px;
        width: 300px;
        height: 400px;

        .poster{
            position: absolute;
            left: 0;
            top: 0;
            min-width: 300px;
            width: 300px;
            height: 400px;
            border-radius:5px ;
        }

        .poster:hover{
            opacity: 0.3;
        }

        .nullo{
            position: absolute;
            left: 0;
            top: 0;
            width: inherit;
            height: inherit;
            background:$main-color;
            h1{
                color: $second-color;
            }
        }

        .nullo:hover{
            opacity: 0.1;
        }
        li{
            color: $second-color;
            opacity: 1;
            img{
                width: 18px;
                height: 18px;
            }            
            .piene{
                color: yellow;
                fill: yellow;
                display: flex;
            }
            .vuote{
                color: white;
                fill: white;
            }
        }
    }
}

</style>