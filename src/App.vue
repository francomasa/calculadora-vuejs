<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Formulario from './components/Formulario.vue';
  
  const estado = reactive({
    numero1: '',
    numero1Temp: 0,
    numero2:'',
    numero2Temp: 0,
    resultado: 0,
    operator: '+',
    error: '',
  });

  const calculate = () => {     
    estado.numero1 = parseFloat(estado.numero1Temp);
    estado.numero2 = parseFloat(estado.numero2Temp);
    console.log(estado);
    switch (estado.operator) {
      case '+':
        estado.resultado = estado.numero1 + estado.numero2;
        break;
      case '-':
        estado.resultado = estado.numero1 - estado.numero2;
        break;
      case '*':
        estado.resultado = estado.numero1 * estado.numero2;
        break;
      case '/':
        if (estado.numero2 === 0) {
          estado.error = 'Não é possivel dividir por 0';
          return ;
        }
        estado.resultado = estado.numero1 / estado.numero2;
        break;
      default:
        return;
    }
    estado.error = '';
  }
</script>

<template>
    <div class="container">
        <Cabecalho />
        <Formulario :fazer-calculo="calculate()" :trocar-operador="evento => estado.operator = evento.target.value" :numero1="estado.numero1" :numero1-temp="evento => estado.numero1Temp = evento.target.value" :numero2="estado.numero2" :numero2-temp="evento => estado.numero2Temp = evento.target.value" :resultado-calculo="estado.resultado" :error="estado.error" />

        
    </div>
</template>

<style scoped>
.invalido {
  color: red;
  font-weight: 500;
}
</style>
