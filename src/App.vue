<script setup>
import { reactive } from "vue";

    const Vue = reactive({
    el: '#app',
    data: {
        numero1: 0,
        numero2: 0,
        operador: 'add',
        resultado: 0
    },
    methods: {
        calculate: function () {
            switch (this.operador) {
                case 'add':
                    this.resultado = parseFloat(this.numero1) + parseFloat(this.numero2);
                    break;
                case 'subtract':
                    this.resultado = parseFloat(this.numero1) - parseFloat(this.numero2);
                    break;
                case 'multiply':
                    this.resultado = parseFloat(this.numero1) * parseFloat(this.numero2);
                    break;
                case 'divide':
                    if (parseFloat(this.numero2) !== 0) {
                        this.resultado = parseFloat(this.numero1) / parseFloat(this.numero2);
                    } else {
                        this.resultado = 'Não é possível dividir por zero';
                    }
                    break;
                default:
                    this.resultado = 0;
            }
        }
    }
})
</script>

<template>
  <div id="app">
        <input type="number" v-model.number="numero1" @input="calculate">
        <select v-model="operador" @change="calculate">
            <option value="add">+</option>
            <option value="subtract">-</option>
            <option value="multiply">*</option>
            <option value="divide">/</option>
        </select>
        <input type="number" v-model.number="numero2" @input="calculate">
        <p>resultado: {{ resultado }}</p>
    </div>
</template>

<style scoped>

</style>
