<template>

    <div id="app">

        <h1>Calculadora do Erik</h1>
        
        <Calculator />

    </div>

</template>

<script>

import Calculator from "./main/Calculator.vue"

export default {

    name: 'App',
    components: { Calculator }

}

</script>

<style>

    * {

        background-image: linear-gradient( rgb(7, 63, 40), rgb( 0, 0, 0 ) )
        
    }
    
    h1 {

        text-align: center;
        color: yellow;
        font-family: "Super Mario 256", sans-serif;
    }

    body {

        background: #31475e !important;

    }

</style>