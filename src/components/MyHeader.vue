<template>
  <header>
      <img src="../assets/mtv-logo.png" alt="">
  </header>
</template>

<script>
export default {
    name: 'MyHeader'
}
</script>

<style lang="scss" scope>
@import '../style/variables.scss';
header {
    height: 60px;
    background-color: $blue;
    display: flex;
    align-items: center;

    img {
        width: 60px;
        margin-left: 20px
    }
}
</style>