<template>
    <div class="card p-3">
        <img :src="disc.poster">
        <div class="card-body p-0 pt-3">
            <h5 class="mb-3">{{disc.title}}</h5>
            <p class="m-0">{{disc.author}}</p>
            <p class="m-0">{{disc.year}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'DiscCard',
    props: {
        disc: Object
    }
}
</script>

<style lang="scss" scope>
@import '../../style/variables.scss';
.card {
    width: 100%;
    background-color: $yellow !important;

    img {
    width: 100%;
    height: auto;
    }

    .card-body {
        width: 100%;
        max-width: 400px;
        color: #fff;
        text-align: center;

        h5 {
            text-transform: uppercase;
            text-shadow: 1px 1px 2px #000;
        }

        p {
            font-size: 0.8rem;
            text-shadow: 1px 1px 2px #000;
        }
    }
}
</style>