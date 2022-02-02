<template>
  <div class="container-fluid d-flex align-items-center">
      <Cerca />
  </div>
</template>

<script>
import Cerca from './commons/Cerca.vue';

export default {
    name:"Header",
    components:{
        Cerca
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/vars.scss';

.container-fluid{
    min-height: 50px;
    background-color: $main-color;
}
</style>