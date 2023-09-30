<template>
    <div class="container">
        <input v-model="campo1" type="text">
        <input v-model="campo2" type="text">
        <select v-model="operacao">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
        </select>
        <p>Resultado: {{ resultado }}</p>
    </div>
</template>


<script setup>
import { ref, watch, reactive } from 'vue';

const campo1 = ref(1);
const campo2 = ref(1);
const operacao = ref('+');
const resultado = ref(0);

watch([campo1, campo2, operacao], () => {
    calcularResultado();
});

function calcularResultado() {
    const num1 = parseFloat(campo1.value);
    const num2 = parseFloat(campo2.value);

    switch (operacao.value) {
        case '+':
            resultado.value = num1 + num2;
            break;
        case '-':
            resultado.value = num1 - num2;
            break;
        case '*':
            resultado.value = num1 * num2;
            break;
        case '/':
            resultado.value = num1 / num2;
            break;
        default:
            resultado.value = 0;
    }
}
</script>


<style scoped>

    * {
        font-weight: bold;
        font-size: 20px;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        padding: 5px;
    }
    .container {
        margin-top: 40vh;
        margin-left: 40vw;
    }

    
</style>

