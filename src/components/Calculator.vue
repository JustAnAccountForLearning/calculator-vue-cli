<template>
    <div class="calc">
        <h1>{{ msg }}</h1>
        <div class="calc-card"></div>
    </div>
</template>

<script defer>
export default {
    name: 'Calculator', 
    props: {
        msg: String
    }
}
</script>

<style scoped>
    .calc-card {
        justify-content: center;
        border: 1px solid black;
        width: 120px;
        height: 160px;
        position: absolute;
        margin: auto;
        border-radius: 8px;
        box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
    }
</style>