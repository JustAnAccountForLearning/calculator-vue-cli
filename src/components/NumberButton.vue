<template>
    <div class="btn">
        <button type="button" class="num-btn"> {{ number }} </button>
    </div>
</template>

<script>
export default {
    name: 'NumberButton', 
    props: {
        number: String,
    }
}
</script>

<style scoped>
    .num-btn {
        text-align: center;
        width: 45px;
        height: 45px;
        margin: 3px;
        position: relative;
        float: left;
        border-radius: 4px;
        color: blue;
        outline: 0;
    }

    .num-btn:hover {
        background-color: white;
    }
</style>