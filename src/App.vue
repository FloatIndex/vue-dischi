<template>
  <div id="app">
    <MyHeader :genres='genresList'/>
    <MyMain @genresReady='getGenresList'/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyMain from './components/MyMain.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
  },
  data() {
    return {
      genresList: []
    }
  },
  methods: {
    getGenresList(genresList) {
      this.genresList = genresList;
    }
  }
}
</script>

<style lang="scss">
@import './style/general.scss';
</style>
