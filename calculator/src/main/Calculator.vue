<template>

    <div class="p-3" style="max-width: 400px; margin: 50px auto; background: #234">

        <!-- Resultado da Calculadora -->
        <div class="w-full rounded m-1 p-3 text-right lead font-weight bold text-white bg-vue-dark">

            {{ calculatorValue || 0 }}

        </div>

        <!-- Botões da Calculadora -->
        <!-- Fileira -->
        <div class="row no-gutters">

            <!-- Coluna -->
            <div class="col-3" v-for="n in calculatorElements" :key="n">

                <div class="lead text-white text-center m-1 py-3 bg-vue-dark rounded hover-class"
                
                    :class="{ 'bg-vue-green': [ 'C', '*', '/', '-', '+', '%', '='].includes( n ) }"
                    @click="action(n)">

                    {{ n }}

                </div>

            </div>

        </div>

    </div>

</template>

<script>

export default {

    name: 'Calculator',
    props: { msg: String },

    data() {

        return {

            calculatorValue: '',
            calculatorElements: [ 'C', '*', '/', '-', 7, 8, 9, '+', 4, 5, 6, '%', 1, 2, 3, '=', 0, '.'],
            operator: null,
            previousCalculatorValue: '',

        }

    },

    methods: {

        action( n ) {
            /* Acrescenta um valor */
            if( !isNaN( n ) || n === '.' ) {

                this.calculatorValue += n + '';

            }

            /* Limpa valor */
            if ( n === 'C' ) {

                this.calculatorValue = '';

            }

            /* Porcentagem */
            if ( n === '%') {

                this.calculatorValue = this.calculatorValue / 100 + '';

            }

            /* Operadores */
            if ( [ '/', '*', '-', '+' ].includes( n ) ) {

                this.operator = n;
                this.previousCalculatorValue = this.calculatorValue;
                this.calculatorValue = '';

            }

            /* Calcula o resultado usando a função eval */
            if ( n === '=' ) {

                this.calculatorValue = eval(

                    this.previousCalculatorValue + this.operator + this.calculatorValue

                );

                this.previousCalculatorValue = '',
                this.operator = null;

            }

        }

    }

}

</script>

<style scoped>

    .bg-vue-dark {

        background: #31475e;

    }

    .hover-class:hover {

        cursor: pointer;
        background: #3D5875;

    }

    .bg-vue-green {

        background: #3fb984;
    }

    div.p-3 {

        background: black;
        border: 2px solid white;

    }

    div.col-3 {

        background: black;
        border: 2px solid white;

    }

</style>