<template>
    <div id="valid">
        <h3>
            Ни одно поле не должно быть пустым! <br>
            А также название товара не должно повторятся!
        </h3>
    </div>
</template>

<script>
    export default {
    }
</script>

<style scoped>
    #valid {
        margin-left: 50px;
    }
    
    #valid > h3 {
        color: #f00
    }
</style>