<template>
  <div>
        <!--
            v-model nella select crea un binding tra il valore selezionato e il dato selectedGenre
            @change emette l'evente changedGenre al cambiare del valore selezionato, passando come parametro il dato selectedGenre 
        -->
        <select v-model="selectedGenre" @change="$emit('changedGenre', selectedGenre)">
            <option value="">Seleziona genere</option>
            <option
                v-for="(genre, index) in genresList" :key="index"
                :value="genre">
                {{genre}}
            </option>
        </select>
  </div>
</template>

<script>
export default {
    name: 'SelectGenre',
    props: {
        genresList: Array
    },
    data() {
        return {
            selectedGenre: ''
        }
    },
    methods: {
        // selectGenre() {
        //     this.$emit("changedGenre", this.search);
        //     console.log("Il figlio passa: " + this.search);
        // }
    },
}
</script>

<style lang="scss" scopes>

</style>