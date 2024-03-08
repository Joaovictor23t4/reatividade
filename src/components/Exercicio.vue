
<template>
    <div v-show="exercicioShow !== 0" class="exit">
        <button @click="exercicioShow = 0; contador = 0; contador2 = 0; valorIdade = null" class="buttonExit">X</button>
    </div>

    <div v-if="exercicioShow === 0" class="container-show-opcoes">
        <div class="container-opcoes">
            <button @click="exercicioShow = 1" class="buttonExibir" style="background-color: red;">Exercicio 1</button>
        </div>
        <div class="container-opcoes">
            <button @click="exercicioShow = 2" class="buttonExibir" style="background-color: blue;">Exercicio 2</button>
        </div>
        <div class="container-opcoes">
            <button @click="exercicioShow = 3" class="buttonExibir" style="background-color: green;">Exercicio 3</button>
        </div>
    </div>

    <div v-else-if="exercicioShow === 1" class="exercicio">
            <div class="container">
              <button @click="contador++" class="liberar-evento">+</button>
              <button v-if="contador > 0" @click="contador--" class="liberar-evento">-</button>
              <button v-else class="bloquear-evento">-</button>
              <button @click="contador = 0"><span class="reload-icon"><svg xmlns="http://www.w3.org/2000/svg" width="25" height="25" fill="currentColor" class="bi bi-arrow-clockwise" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M8 3a5 5 0 1 0 4.546 2.914.5.5 0 0 1 .908-.417A6 6 0 1 1 8 2z"/>
            <path d="M8 4.466V.534a.25.25 0 0 1 .41-.192l2.36 1.966c.12.1.12.284 0 .384L8.41 4.658A.25.25 0 0 1 8 4.466"/>
            </svg></span></button>
            </div>
            <p>Valor do contador: {{ contador }}</p>
            <div class="container">
              <button @click="contador2++" class="liberar-evento">+</button>
              <button v-if="contador2 > 0" @click="contador2--" class="liberar-evento">-</button>
              <button v-else class="bloquear-evento">-</button>
              <button @click="contador2 = 0"><span class="reload-icon"><svg xmlns="http://www.w3.org/2000/svg" width="25" height="25" fill="currentColor" class="bi bi-arrow-clockwise" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M8 3a5 5 0 1 0 4.546 2.914.5.5 0 0 1 .908-.417A6 6 0 1 1 8 2z"/>
            <path d="M8 4.466V.534a.25.25 0 0 1 .41-.192l2.36 1.966c.12.1.12.284 0 .384L8.41 4.658A.25.25 0 0 1 8 4.466"/>
            </svg></span></button>
            </div>
            <p>Valor do contador: {{ contador2 }}</p>
            <div class="soma">Valor da <strong>soma</strong> dos contadores: {{ soma }}</div>
            <div class="somaMaior" v-if="soma > 10">A soma dos contadores é maior que 10</div>
            <div class="somaIgual" v-if="soma === 10">A soma dos contadores é igual a 10</div>
            <div class="somaMenor" v-if="soma < 10">A soma dos contadores é menor que 10</div>
    </div>

    <div v-else-if="exercicioShow === 2" class="exercicio">
            <div class="container">
              <button @click="contador++" class="liberar-evento">+</button>
              <button v-if="contador > 0" @click="contador--" class="liberar-evento">-</button>
              <button v-else class="bloquear-evento">-</button>
              <button @click="contador = 0"><span class="reload-icon"><svg xmlns="http://www.w3.org/2000/svg" width="25" height="25" fill="currentColor" class="bi bi-arrow-clockwise" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M8 3a5 5 0 1 0 4.546 2.914.5.5 0 0 1 .908-.417A6 6 0 1 1 8 2z"/>
            <path d="M8 4.466V.534a.25.25 0 0 1 .41-.192l2.36 1.966c.12.1.12.284 0 .384L8.41 4.658A.25.25 0 0 1 8 4.466"/>
            </svg></span></button>
            </div>
            <p>Valor do contador: {{ contador }}</p>
            <div class="container">
              <button @click="contador2++" class="liberar-evento">+</button>
              <button v-if="contador2 > 0" @click="contador2--" class="liberar-evento">-</button>
              <button v-else class="bloquear-evento">-</button>
              <button @click="contador2 = 0"><span class="reload-icon"><svg xmlns="http://www.w3.org/2000/svg" width="25" height="25" fill="currentColor" class="bi bi-arrow-clockwise" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M8 3a5 5 0 1 0 4.546 2.914.5.5 0 0 1 .908-.417A6 6 0 1 1 8 2z"/>
            <path d="M8 4.466V.534a.25.25 0 0 1 .41-.192l2.36 1.966c.12.1.12.284 0 .384L8.41 4.658A.25.25 0 0 1 8 4.466"/>
            </svg></span></button>
            </div>
            <p>Valor do contador: {{ contador2 }}</p>
            <div class="soma">Valor da <strong>soma</strong> dos contadores: {{ soma }}</div>
            <div class="somaMaior" v-if="ePar && soma !== 0">A soma dos contadores é par</div>
            <div class="somaMenor" v-else-if="ePar === false && soma !== 0">A soma dos contadores é ímpar</div>
    </div>

    <div v-else-if="exercicioShow === 3" class="exercicio">
            <div class="container">
                <div class="container-input">
                    <label for="">Informe sua idade:</label>
                    <input type="text" placeholder="Informe sua idade" v-model="valorIdade">
                </div>

                <div v-if="valorIdade">Você é maior de idade: {{ eAdulto }}</div>
            </div>
    </div>
  </template>
  
  <script setup>
  import { ref, reactive, computed, watchEffect } from 'vue'
  
  const exercicioShow = ref(0);
  const contador = ref(0);
  const contador2 = ref(0);
  const valorIdade = ref(null);

  const soma = computed(() => {
    return contador.value + contador2.value
  })

  const ePar = computed(() => {
    return ((contador.value + contador2.value) % 2 === 0) ? true : false
  })

  const eAdulto = computed(() => {
    return (valorIdade.value >= 18) ? 'Verdadeiro!' : 'Falso!';
  })
  </script>
  
  <style scoped>
  button {
    width: 50px;
    border: none;
    font-size: 2rem;
  }

  .exit {
    position: absolute;
    top: 0;
    right: 0;
    margin: 10px 10px 0 0;
  }

  .buttonExit {
    cursor: pointer;
  }
  
  .container-show-opcoes {
    display: flex;
    justify-content: flex-start;
    gap: 10px;
  }

  .exercicio {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 20px;
  }

  .container {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
  }

  .container-input > label {
    position: relative;
    right: 5px;
  }

  .reload-icon {
    position: relative;
    bottom: 1px;
    cursor: pointer;
  }
  
  .liberar-evento {
    color: blue;
    cursor: pointer;
  }
  
  .bloquear-evento {
    color: black;
    opacity: .5;
    cursor: not-allowed;
  }

  .somaMaior {
    background-color: green;
    color: #fdfdfd;
    padding: 10px;
  }

  .somaIgual {
    background-color: blue;
    color: #fdfdfd;
    padding: 10px;
  }

  .somaMenor {
    background-color: red;
    color: #fdfdfd;
    padding: 10px;
  }

  .somaMaior, .somaIgual, .somaMenor {
    margin-left: 10px;
  }

  .buttonExibir {
    color: #fdfdfd;
    font-size: 1.8rem;
    width: 200px;
    cursor: pointer;
  }
  </style>