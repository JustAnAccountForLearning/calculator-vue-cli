<template>
    <div class="screen">
        <h2 class="screen-card">
            {{ msg }}
        </h2>
    </div>
</template>

<script>
export default {
    name: 'CalcScreen', 
    props: {
        msg: String
    }
}
</script>

<style scoped>
    .screen-card {
        text-align: right;
        border: 1px solid black;
        border-radius: 3px;
        width: 200px;
        margin-top: 0;
        height: 30px;
 
    }
</style>