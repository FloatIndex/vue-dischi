<template>
  <div id="app">
    <!-- genresList passato tramite props genres a header -->
    <MyHeader :genres='genresList' @changedGenre='startSearch'/>
    <MyMain @genresReady='getGenresList' :genreToSearch='genreToSearch'/>
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
      genresList: [],
      genreToSearch: ''
    }
  },
  methods: {
    //l'argomento genresFromMain della funzione è passato direttamente dall'evento genresReady del main
    getGenresList(genresFromMain) {
      this.genresList = genresFromMain;
    },

    //l'argomento genreFilterFromHeader della funzione è passato direttamente dall'evento changedGenre dell'header
    startSearch(genreFilterFromHeader) {
      this.genreToSearch = genreFilterFromHeader;
    }
  }
}
</script>

<style lang="scss">
@import './style/general.scss';
</style>
