<template>
  <header>
      <img src="../assets/mtv-logo.png" alt="">
      <SelectGenre : @change="makeResearch"/>
  </header>
</template>

<script>
import SelectGenre from './partials/SelectGenre.vue';

export default {
    name: 'MyHeader',
    props: {
        genres: Array
    },
    components: {
        SelectGenre
    },
    data() {
        return {
            selectGenres: []
        }
    },
    methods: {
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';
header {
    height: 60px;
    background-color: $blue;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0px 20px;


    img {
        width: 60px;
    }
}
</style>