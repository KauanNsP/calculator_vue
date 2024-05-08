<template>
  <div class="calculadora">
    <input type="number" v-model="numero1" @input="calcularResultado">
    <select v-model="operacao" @change="calcularResultado">
      <option value="adição+">+</option>
      <option value="subtração-">-</option>
      <option value="multiplicação*">*</option>
      <option value="divisão/">/</option>
    </select>
    <input type="number" v-model="numero2" @input="calcularResultado">
    <div>Seu resultado é: {{ resultado }} !</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: '+',
      resultado: 0
    };
  },
  methods: {
    calcularResultado() {
      switch (this.operacao) {
        case 'adição+':
          this.resultado = parseFloat(this.numero1) + parseFloat(this.numero2);
          break;
        case 'subtração-':
          this.resultado = parseFloat(this.numero1) - parseFloat(this.numero2);
          break;
        case 'multiplicação*':
          this.resultado = parseFloat(this.numero1) * parseFloat(this.numero2);
          break;
        case 'divisão/':
          this.resultado = parseFloat(this.numero1) / parseFloat(this.numero2);
          break;
        default:
          this.resultado = 0;
      }
    }
  }
};
</script>

<style>
.calculadora {
  display: flex;
  flex-direction: column;
  align-items: center;
}
input, select {
  margin: 5px solid green;
}

body {
  background: linear-gradient(to right, #ccc, rgb(130, 235, 235));
}
</style>