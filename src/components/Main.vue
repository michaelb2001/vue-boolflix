<template>
  <div class="container-fluid">
      <Header />
  </div>
</template>

<script>
import Header from './componets/Header.vue';

export default {
    name:"Main",
    components:{
        Header
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/vars.scss';

</style>