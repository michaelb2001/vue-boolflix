<template>
  <div class="container-fluid d-flex flex-wrap align-items-center justify-content-center">
      <ul>
        <li v-for="(element,index) in lista" :key="index">
            {{element.title}} {{element.name}} <br> 
            {{element.original_title}} {{element.original_name}} <br>
            <img v-if="element.original_language == 'en' " src="../assets/img/en.png">
            <img v-else-if="element.original_language == 'it' " src="../assets/img/it.png"> 
            <img v-else-if="element.original_language == 'de' " src="../assets/img/de.png">  
            <img v-else src="../assets/img/peace.jpg"> <br> 
            {{element.vote_average}}
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
            lingua : ""
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
        display: flex;
        flex-wrap: wrap;


        li{
            color: $second-color;
            text-decoration: none;
            margin: 20px;
            padding: 5px;
            width: 200px;
            height: 250px;
            border: 2px solid white;
            border-radius: 5px;
            img{
                width: 18px;
                height: 18px;
            }
        }
    }
}
</style>