<template>
    <main>
        <div class="container">
            
            <div class="row gy-3 row-cols-1 row-cols-sm-2 row-cols-lg-4 row-cols-xl-5">
                <div class="col" v-for="(disc, index) in filteredDiscList" :key="index">
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
    props: {
        genreToSearch: String
    },
    components: {
        DiscCard,
        LoadingInProgress
    },
    data() {
        return {
            discList: [],
            genres: [],
            loading: true
        }
    },
    computed: {
        filteredDiscList() {
            if(this.genreToSearch == "") {
                return this.discList;
            } else {
                return this.discList.filter(disc => {
                    return disc.genre.includes(this.genreToSearch);
                });
            }
        }
    },
    methods: {
        addDisc() {
            const axios = require('axios');

            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((response) => {
                this.discList = response.data.response;
                this.loading = false;
                
                this.discList.forEach(disc => {
                    if (!this.genres.includes(disc.genre)) {
                        this.genres.push(disc.genre);
                    }
                });
                this.$emit('genresReady', this.genres);
                // handle success
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
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