<template>
  <div class="container-fluid d-flex align-items-center justify-content-between">
      <h1 class="text-danger">BOOLFIX</h1>
      <Cerca 
      @cerca="chiamaEmit"/>
  </div>
</template>

<script>
import Cerca from './commons/Cerca.vue';

export default {
    name:"Header",
    components:{
        Cerca
    },
    methods:{
        chiamaEmit: function(valore){
            this.$emit('chiama2', valore );
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/vars.scss';

.container-fluid{
    width: 100%;
    min-height: 50px;
    background-color: $main-color;
}
</style>