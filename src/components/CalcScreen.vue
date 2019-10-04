<template>
    <div class="screen">
        <div class="screen-card"></div>
    </div>
</template>

<script>
export default {
    name: 'CalcScreen', 
    props: {
        msg: String //value
    }
}

//let value = '0';
</script>

<style scoped>
    .screen-card {
        border: 1px solid black;
        width: 100px;
        margin: auto;
        position: absolute;
        height: 30px;
        z-index: 1;
    }
</style>