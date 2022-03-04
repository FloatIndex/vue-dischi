<template>
  <div>
      <select @change="$emit('changedGenre', search)"></select>
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
            
        }
    },
    methods: {
        // selectGenre() {
        //     this.$emit("changedGenre", this.search);
        //     console.log("Il figlio passa: " + this.search);
        // }
    }
}
</script>

<style lang="scss" scopes>

</style>