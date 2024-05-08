<script setup>
import { reactive } from "vue";

    const Vue = reactive({
    el: '#app',
    data: {
        num1: 0,
        num2: 0,
        operator: 'add',
        result: 0
    },
    methods: {
        calculate: function () {
            switch (this.operator) {
                case 'add':
                    this.result = parseFloat(this.num1) + parseFloat(this.num2);
                    break;
                case 'subtract':
                    this.result = parseFloat(this.num1) - parseFloat(this.num2);
                    break;
                case 'multiply':
                    this.result = parseFloat(this.num1) * parseFloat(this.num2);
                    break;
                case 'divide':
                    if (parseFloat(this.num2) !== 0) {
                        this.result = parseFloat(this.num1) / parseFloat(this.num2);
                    } else {
                        this.result = 'Não é possível dividir por zero';
                    }
                    break;
                default:
                    this.result = 0;
            }
        }
    }
})
</script>

<template>
  <div id="app">
        <input type="number" v-model.number="num1" @input="calculate">
        <select v-model="operator" @change="calculate">
            <option value="add">+</option>
            <option value="subtract">-</option>
            <option value="multiply">*</option>
            <option value="divide">/</option>
        </select>
        <input type="number" v-model.number="num2" @input="calculate">
        <p>Resultado: {{ result }}</p>
    </div>
</template>

<style scoped>

</style>
