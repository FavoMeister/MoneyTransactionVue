<script setup lang="ts">
import type { Transaccion } from '@/types/types';

type PropTypes = {
    transacciones: Transaccion[]
};

defineProps<PropTypes>();

const emit = defineEmits<{
  (e: 'eliminar-transaccion',transaccionId:number):void
}>();

const eliminarTransaccion = (transaccionId:number)=>emit('eliminar-transaccion',transaccionId);

</script>
<template>
    <div class="row mt-3">
      <div class="col">
        <h2 class="border-bottom border-success pb-2">
          <i class="fa-solid fa-timeline"></i>&nbsp;Historial Transacciones
        </h2>
        <!-- Transactions -->
        <div class="card mb-1 fw-bold" :class="transaccion.costo < 0 ? 'border-danger text-danger' : 'border-success text-success'" v-for="transaccion in transacciones" :key="transaccion.id">
          <div class="card-body">
            <div class="row">
              <div class="col-5">
                {{ transaccion.nombre }}
              </div>
              <div class="col-5">
                {{ transaccion.costo }}
              </div>
              <div class="col-2">
                <button class="btn btn-danger border" aria-label="Eliminar"
                  @click="eliminarTransaccion(transaccion.id)"><i class="fa-solid fa-trash"></i></button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>