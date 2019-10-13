<template>
    <div class="screen">
        <h2 style="position: relative; z-index: 4;" id="screen-card">
            {{ msg }}
        </h2>
    </div>
</template>

<script>
export default {
    name: 'CalcScreen', 
    props: {
        msg: String,
        backgroundActive: String
    },
    methods: {
        setColor: function(value) {
            document.getElementById("screen-card").style.backgroundColor = value;
        }
    },
    watch: {
        'backgroundActive': function() {
            this.setColor(this.backgroundActive);
        }
    }
}
</script>

<style scoped>
    #screen-card {
        position: relative;
        overflow: hidden;
        text-align: right;
        border: 1px solid rgb(83, 83, 83);
        border-radius: 3px;
        padding-right: 4px;
        width: 196px;
        margin-top: 0;
        height: 30px;
        z-index: 4;
        background-color: rgba(255, 255, 255, 0.801);
        box-shadow: inset 0 0 2px #000000;
    }
</style>