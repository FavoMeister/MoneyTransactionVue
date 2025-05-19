
<script setup lang="ts">
import type { Transaccion } from '@/types/types';
import { ref } from 'vue';
import {useToast} from 'vue-toastification';

const concepto = ref('');
const costo = ref(0);
const toast = useToast();

const emit = defineEmits<{
  (e:'agregar-transaccion',transaccion:Transaccion):void // el método no retornará nada
}>();

const guardar = ()=>{
  if(!concepto.value||!costo.value){
    toast.error('Ambos valores deben ser llenados')
    return;
  }

  const transaccion = {
    id:0,
    nombre: concepto.value,
    costo: costo.value
  }

  //TODO: Emitir evento personalizado del elemento hijo al padre
  emit('agregar-transaccion',transaccion);
  //Limpiamos los valores después de emitirlos
  concepto.value='';
  costo.value=0;
}
</script>
<template>
    <div class="row mt-3">
      <div class="col">
        <h2 class="border-bottom border-primary pb-2">
          <i class="fa-regular fa-calendar-plus"></i>&nbsp;Agregar transacción
        </h2>
        <form @submit.prevent.stop="guardar">
          <div class="mb-3">
            <label for="concepto" class="form-label">Concepto</label>
            <input type="text" class="form-control" id="concepto" aria-describedby="conceptoHelp" v-model="concepto"/>
          </div>
          <div class="mb-3">
            <label for="cantidad" class="form-label">Cantidad</label>
            <input type="text" class="form-control" id="cantidad" aria-describedby="cantidadHelp" v-model.number="costo"/>
            <div id="cantidadHelp" class="form-text fw-bold">
              Cantidad positiva(+): ingreso, cantidad negativa(-): gasto.
            </div>
          </div>
          <div class="d-grid">
            <button type="submit" class="btn btn-lg btn-primary" aria-label="Agregar"><i
                class="fa-solid fa-plus"></i>&nbsp;Agregar</button>
          </div>
        </form>
      </div>
    </div>
</template>