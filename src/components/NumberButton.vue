<template>
    <div class="btn">
        <button @click="$emit('update')" type="button" class="num-btn"> {{ number }} </button>
    </div>
</template>

<script>
export default {
    name: 'NumberButton', 
    props: {
        number: String,
    },
    methods: {
        
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
        border-radius: 6px;
        font-weight: 600;
        font-size: 16px;
        color: rgba(0, 0, 165, 0.863);
        outline: 0;
        box-shadow: inset 0 0 2px #3b3b3b;
    }

    .num-btn:hover {
        background-color: white;
    }
</style>