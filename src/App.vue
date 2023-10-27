<script setup>
import { computed, reactive } from "vue";

const title = "Calculadora Aritmética";

const state = reactive({
  input1: "",
  input2: "",
  operator: "addition",
});

function result() {
  let { input1, input2 } = state;
  const { operator } = state;

  if (input1 == "" && input2 == "") {
    input1 = 0;
    input2 = 0;
  } else if (input1 === "") {
    input1 = 0;
  } else if (input2 === "") {
    input2 = 0;
  }

  switch (operator) {
    case "addition":
      return parseFloat(input1) + parseFloat(input2);
    case "subtraction":
      return parseFloat(input1) - parseFloat(input2);
    case "multiplication":
      return parseFloat(input1) * parseFloat(input2);
    case "division":
      return parseFloat(input1) / parseFloat(input2);
  }
}
</script>

<template>
  <body class="">
    <div class="container">
      <header class="p-5 mb-2 mt-4 text-center">
        <h1 class="text-light border border-secondary rounded-5 p-3">
          {{ title }}
        </h1>
        <i class="bi bi-calculator-fill fs-1"></i>
      </header>
      <div class="p-5 mb-4 mt-1 rounded-5 bg-light">
        <div class="container-sm">
          <form>
            <h3 class="text-center mb-5">Faça cálculos matemáticos abaixo:</h3>
            <div class="row">
              <div class="col">
                <input
                  type="number"
                  placeholder="0"
                  class="pb-1 pt-1 text-center rounded-4"
                  @keyup="(event) => (state.input1 = event.target.value)"
                />
              </div>
              <div class="col text-center">
                <select
                  class="text-center form-control rounded-4 pb-1.8 pt-1 align-middle fs-6 text-uppercase"
                  @change="(event) => (state.filter = event.target.value)"
                >
                  <option value="addition" id="addition">Adição +</option>
                  <option value="subtraction" id="subtraction">
                    Subtração -
                  </option>
                  <option value="multiplication" id="multiplication">
                    Multiplicação *
                  </option>
                  <option value="division" id="division">Divisão /</option>
                </select>
              </div>
              <div class="col">
                <input
                  type="number"
                  placeholder="0"
                  class="pb-1 pt-1 text-center rounded-4"
                  @keyup="(event) => (state.input2 = event.target.value)"
                />
              </div>
            </div>
            <div class="results row-2 text-center mt-5">
              <h4>O resultado da conta é:</h4>
              <div class="number">
                {{ result() }}
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
    <footer>
      <div class="container text-center mt-5">
        <p>Desenvolvido por David Vilela</p>
        <p>&copy;Todos os direitos reservados - 2023</p>
        <p>
          <a href="https://github.com/davidvilela1988"
            >https://github.com/davidvilela1988</a
          >
        </p>
      </div>
    </footer>
  </body>
</template>

<style scoped>
body {
  background-color: black;
}

i {
  color: aliceblue;
}

.container-sm {
  max-width: 650px;
}

.form-control {
  background-color: rgb(68, 68, 68);
  color: aliceblue;
}

.number {
  font-size: 46px;
  font-weight: bold;
  margin-top: 10px;
}

footer {
  color: aliceblue;
}
</style>
