<template>
    <div class="loading">
        <h1>loading...</h1>
    </div>
</template>

<script>
export default {
    name: 'LoadingInProgress'
}
</script>

<style lang="scss" scope>
@import '../../style/variables.scss';

.loading {
    width: 100%;
    height: 100%;
    background-color: $grey;
    display: flex;
    justify-content: center;
    align-items: center;

    h1 {
        font-size: 3rem;
        text-transform: uppercase;
        color: #fff;
    }
}
</style>