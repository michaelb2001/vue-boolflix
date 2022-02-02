<template>
  <div class="container d-flex align-items-center justify-content-center mx-2">
      <input type="text" placeholder="write a title" class="rounded-pill px-2 py-0 mx-2">

      <button class="btn btn-danger rounded-pill px-2 py-0">Search</button>
  </div>
</template>

<script>
export default {
    name:"Cerca"

}
</script>

<style lang="scss" scoped>
@import '../../assets/vars.scss';
input{
    background-color: $second-color;
    color: $main-color;
}
</style>