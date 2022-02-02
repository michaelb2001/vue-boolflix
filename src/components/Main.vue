<template>
  <div class="container-fluid d-flex flex-wrap align-items-center justify-content-center">
      <ul>
          <li v-for="(element,index) in listaFilms" :key="index">
              {{element.title}} , {{element.original_title}} , 
              {{element.original_language}} , {{element.vote_average}}
          </li>
      </ul>
  </div>
</template>

<script>
export default {
    name:"Main",
    props:{
        listaFilms :Array
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
        }
    }
}
</style>