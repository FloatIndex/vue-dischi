<template>
  <header>
        <img src="../assets/mtv-logo.png" alt="">
        <!--
            header passa a select genres tramite props genresList
            select passa a header(che sta in ascolto dell'evento @changedGenre) l'argomento della funzione getChangedGenre
        -->
        <SelectGenre :genresList="genres" @changedGenre='getChangedGenre'/>
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
            genreFilter: ''
        }
    },
    methods: {
        // selectedGenreFromSelect è l'argomento della funzione getChangedGenre
        getChangedGenre(selectedGenreFromSelect) {
            this.genreFilter = selectedGenreFromSelect;
            // header a questo punto emette l'evento changedGenre da passare ad app, che lo passerà poi a main
            this.$emit('changedGenre', this.genreFilter);
        }
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