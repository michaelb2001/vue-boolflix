<template>
  <div class="container-fluid d-flex flex-wrap align-items-start justify-content-center">
      <ul v-for="(element,index) in lista" :key="index">
        <div>
            <img v-if="element.poster_path != null" class="poster" :src="apiIMG+element.poster_path" alt="">
        </div>
        <div class="nullo d-flex justify-content-center align-items-center text-center" v-if="element.poster_path == null ">
            <h1>{{element.title}} {{element.name}}</h1>
        </div>
        <li>{{element.title}} {{element.name}}</li>
        <li>{{element.original_title}} {{element.original_name}} </li>
        <li><img v-if="element.original_language == 'en' " src="../assets/img/en.png">
            <img v-else-if="element.original_language == 'it' " src="../assets/img/it.png"> 
            <img v-else-if="element.original_language == 'de' " src="../assets/img/de.png">  
            <img v-else src="../assets/img/peace.jpg">
        </li>
        <li v-for="elemento in numero_stelline" :key="elemento.id">
            <i class="fas fa-star"></i>
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
            numero_stelline: null,
            apiIMG : "https://image.tmdb.org/t/p/w300"
        }
    },
    mounted(){
        this.stelline;
    },
    methods:{
        stelline: function(){
            this.numero_stelline = Math.trunc(this.lista.vote_average / 2 );
            console.log(this.numero_stelline);
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
            i{
                color: yellow;
            }
        }
    }
}

.fa-arrow-alt-circle-left{
    position:absolute;
    top: 50%;
    left:10px;
    color:$second-color;
    font-size:24px

}

.fa-arrow-alt-circle-right{
    position:absolute;
    top: 50%;
    right:10px;
    color:$second-color;
    font-size:24px;
}
</style>