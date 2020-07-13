<template>
  <div class="loading">
    <img alt="Vue logo" src="../assets/images/sunny-light.svg" class="logo">
  </div>
</template>

<script>
export default {
  name: 'Preloading'
}
</script>

<style lang="scss">
  .loading{
    position: fixed;
    background: black;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>
