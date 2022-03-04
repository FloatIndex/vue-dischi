<template>
    <main>
        <div class="container">
            
            <div class="row gy-3 row-cols-1 row-cols-sm-2 row-cols-lg-4 row-cols-xl-5">
                <div class="col" v-for="(disc, index) in discList" :key="index">
                    <DiscCard :disc="disc"/>
                </div>
            </div>
        </div>
        <LoadingInProgress v-if="loading"/>
    </main>
</template>

<script>
import DiscCard from './partials/DiscCard.vue';
import LoadingInProgress from './partials/LoadingInProgress.vue';

export default {
    name: 'MyMain',
    components: {
        DiscCard,
        LoadingInProgress
    },
    data() {
        return {
            discList: [],
            genresList: [],
            loading: true
        }
    },
    methods: {
        addDisc() {
            const axios = require('axios');

            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((response) => {
                this.discList = response.data.response;
                this.loading = false;
                this.getGenres();
                //console.log(this.discList); //confronta log
                this.$emit('genresReady', this.genresList);
                // handle success
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
        },
        getGenres() {
            this.discList.forEach(disc => {
                if (!this.genresList.includes(disc.genre)) {
                    this.genresList.push(disc.genre);
                }
            });
            //console.log(this.genresList); //confronta log
        }
    },
    mounted() {
        this.addDisc();
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';
main {
    height: calc(100vh - 60px);
    background-color: $grey;
    padding: 70px 0px;
    overflow-y: scroll;

    .col {
        display: flex;
        flex-wrap: wrap;
    }
}
</style>