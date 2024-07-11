<template>
  <div class="calculator-bg">
    <div class="container pt-5">
      <div class="card">
        <div class="card-header bg-info text-white">
          <h1 class="text-center">Calculadora Aritmética</h1>
        </div>
        <div class="card-body">
          <div class="row align-items-center">
            <div class="col-md-4">
              <b-form-input v-model.number="num1" @input="calculate" type="number" placeholder="Número 1"></b-form-input>
            </div>
            <div class="col-md-4">
              <b-form-select v-model="operator" @change="calculate">
                <option value="+">+</option>
                <option value="-">-</option>
                <option value="*">*</option>
                <option value="/">/</option>
              </b-form-select>
            </div>
            <div class="col-md-4">
              <b-form-input v-model.number="num2" @input="calculate" type="number" placeholder="Número 2"></b-form-input>
            </div>
          </div>
          <div class="row mt-3">
            <div class="col">
              <h3 class="text-center">Resultado: {{ result }}</h3>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operator: '+',
      result: 0
    };
  },
  watch: {
    num1: 'calculate',
    num2: 'calculate',
    operator: 'calculate'
  },
  methods: {
    calculate() {
      const n1 = parseFloat(this.num1);
      const n2 = parseFloat(this.num2);

      switch (this.operator) {
        case '+':
          this.result = n1 + n2;
          break;
        case '-':
          this.result = n1 - n2;
          break;
        case '*':
          this.result = n1 * n2;
          break;
        case '/':
          this.result = n1 / n2;
          break;
        default:
          this.result = 0;
      }
    }
  }
};
</script>

<style scoped>
.calculator-bg {
  background-image: url('https://source.unsplash.com/1600x900/?calculator');
  background-size: cover;
  background-position: center;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  width: 400px;
  max-width: 100%;
  border: none;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
}

.card-header {
  border-radius: 10px 10px 0 0;
}

.card-body {
  background-color: rgba(255, 255, 255, 0.9);
  border-radius: 0 0 10px 10px;
}

.b-form-input, .b-form-select {
  font-size: 1.2rem;
  padding: 1rem;
  border-radius: 5px;
}

.b-form-select {
  cursor: pointer;
}

h1, h3 {
  font-family: 'Roboto', sans-serif;
}

</style>
