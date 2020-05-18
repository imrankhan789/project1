<template>
    <div id="app">
        <h1>hello world</h1>
        <Calculator></Calculator>
    </div>
</template>
<script>
    import Calculator from  './components/Calculator.vue'
    export default{
        name:'App',
       components:{
           Calculator
       }
    }
</script>

<style>
    #app{
        background-color: slategrey;
    }
    
</style>

