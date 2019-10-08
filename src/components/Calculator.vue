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
        border: 1px solid rgb(100, 100, 100);
        width: 240px;
        height: 350px;
        position: absolute;
        border-radius: 8px;
        box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
    }

    .class {
        text-align: center;
        z-index: 0;
    }
</style>