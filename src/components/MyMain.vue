<template>
    <main>
        <div class="container">
            <div class="row gy-3 row-cols-1 row-cols-sm-2 row-cols-lg-4 row-cols-xl-5">
                <div class="col" v-for="(disc, index) in discList" :key="index">
                    <DiscCard :disc="disc"/>
                </div>
            </div>
        </div>
        <LoadingInProgress  v-if="loading"/>
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
            loading: true
        }
    },
    methods: {
        addDisc() {
            const axios = require('axios');

            // Make a request for a user with a given ID
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((response) => {
                this.discList = response.data.response;
                this.loading = false;
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

<style lang="scss" scope>
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