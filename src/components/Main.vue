<template>
  <div class="container-fluid d-flex flex-wrap align-items-start justify-content-start">
      <ul v-for="(element,index) in lista" :key="index">
        <li>{{element.title}} {{element.name}}</li>
        <li>{{element.original_title}} {{element.original_name}} </li>
        <li><img v-if="element.original_language == 'en' " src="../assets/img/en.png">
            <img v-else-if="element.original_language == 'it' " src="../assets/img/it.png"> 
            <img v-else-if="element.original_language == 'de' " src="../assets/img/de.png">  
            <img v-else src="../assets/img/peace.jpg">
        </li>
        <li>{{element.average_vote}}</li>
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
            numero_stelline: null
        }
    },
    mounted(){
        this.stelline;
    },
    methods:{
        stelline: function(){
            this.numero_stelline = Math.trunc(this.lista.average_vote / 2 );
            console.log(this.numero_stelline);
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
        border: 2px solid $second-color;
        border-radius: 5px;
        padding: 5px;
        margin:20px;
        display:flex;
        flex-direction: column; 
        flex-wrap: wrap;
        width: 200px;
        min-height: 250px;
        li{
           
            color: $second-color;
            img{
                width: 18px;
                height: 18px;
            }

            span{

                i{
                    color: yellow;
                }
            };
        }
    }
}
</style>