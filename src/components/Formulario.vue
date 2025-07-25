
<script setup>
    const props = defineProps(['fazerCalculo', 'trocarOperador', 'numero1', 'numero1Temp', 'numero2','numero2Temp', 'resultadoCalculo', 'error']);
</script>

<template>
    <!-- 
    para fazer o submit do formulario sem atualizar
    o site, usamos o .prevent
       -->
    <form @submit.prevent="props.fazerCalculo">
            <div class="row">
                <div class="col-md-2">
                    <input :value="props.numero1" @keyup="props.numero1Temp" required
                        type="number" class="form-control" placeholder="Numero 1" />
                </div>
                <div class="col-md-2 mt-2">
                    <select @change="props.trocarOperador" class="from-control">
                        <option value="+">+ Soma</option>
                        <option value="-"> - Resta</option>
                        <option value="*"> * Multiplicação</option>
                        <option value="/"> / Divição</option>
                    </select>
                </div>
                <div class="col-md-2">
                    <input :value="props.numero2" @keyup="props.numero2Temp" required
                        type="number" class="form-control" placeholder="Numero 2" @change="props.fazerCalculo" />
                </div>
                <div class="col-md-4 mt-2">
                    <span> = {{ props.resultadoCalculo }}</span>
                </div>
                <div class="col-md-12 mt-2 ms-2">
                    <span class="invalido">{{ props.error }}</span>
                </div>
            </div>
        </form>
</template>

<style scoped>
.invalido {
  color: red;
  font-weight: 500;
}
</style>