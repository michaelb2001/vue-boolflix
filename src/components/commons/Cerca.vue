<template>
  <div class="container d-flex flex-wrap align-items-center justify-content-end mx-2">
    <input id="inputText" type="text" placeholder="write a title" class="rounded-pill px-2 py-0 mx-2"
    v-model="ricercato">
    <button class="btn btn-danger rounded-pill px-2 py-0" 
    @click="$emit('cerca',ricercato)">Search</button>
  </div>
</template>

<script>
export default {
    name:"Cerca",
    data(){
        return{
            ricercato:""
        }
    }

}
</script>

<style lang="scss" scoped>
@import '../../assets/vars.scss';
input{
    background-color: $second-color;
    color: $main-color;
}

img{
    width: 100%;
}

</style>