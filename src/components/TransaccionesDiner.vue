<script setup lang="ts">
import EncabezadoApp from './EncabezadoApp.vue';
import BalanceApp from './BalanceApp.vue';
import NumeroTransaccionesApp from './NumeroTransaccionesApp.vue';
import ResumenApp from './ResumenApp.vue';
import HistorialTransaccionesApp from './HistorialTransaccionesApp.vue';
import AgregarTransaccionApp from './AgregarTransaccionApp.vue';

import { computed, ref } from 'vue';
import type { Transaccion } from '@/types/types';
import {useToast} from 'vue-toastification';
const toast = useToast();

const transacciones = ref<Transaccion[]>([
    {
        id: 1,
        nombre: 'Salario',
        costo: 10000
    },
    {
        id: 2,
        nombre: 'Guitarra Fender',
        costo: -10000
    },
    {
        id: 3,
        nombre: 'Venta Punto de venta',
        costo: 60000
    },
    {
        id: 4,
        nombre: 'Compra Guitarra Acústica',
        costo: -10000
    },
    {
        id: 5,
        nombre: 'Compra Cuerdas Guitarra',
        costo: -10000
    }
]);

//Métodos
const agregarTransaccion = (transaccion: Transaccion) =>{
  transaccion.id = transacciones.value.length+1;
  transacciones.value.push(transaccion);
  toast.success('Transacción agregada exitosamente');
}

const eliminarTransaccion =(transaccionId:number)=>{
  transacciones.value = transacciones.value.filter(
    (transaccion)=> transaccion.id!==transaccionId
  );
  toast.success('Transacción eliminada.');
}

// Computed
const total = computed(() => {
  return transacciones.value.reduce((suma, transaccion) => {
    return suma + transaccion.costo
  }, 0);
});

// Balance Computed
const totalTransactions = computed(() => {
  return transacciones.value.length;
});

const ingresos = computed(()=>{
  return transacciones.value
        .filter((transaccion) => transaccion.costo > 0)
        .reduce((acc,transaccion)=>{
          return acc +transaccion.costo
        },0)
})

const gastos = computed(()=>{
  return transacciones.value
        .filter((transaccion) => transaccion.costo < 0)
        .reduce((acc,transaccion)=>{
          return acc +transaccion.costo
        },0)
})

</script>

<template>
<div class="container">
  <!--Encabezado-->
    <EncabezadoApp/>
    <!--/Encabezado-->
    <div class="row mt-3">
      <!--Balance-->
      <BalanceApp :total="total"/>
      <!--/Balance-->
      <!--NumeroTransacciones-->
      <NumeroTransaccionesApp :total-transacciones="totalTransactions"/>
      <!--/NumeroTransacciones-->
    </div>
    <div class="border-bottom border-primary">
    </div>
    <!--Resumen-->
    <ResumenApp :ingresos="ingresos" :gastos="gastos"/>
    <!--/Resumen-->
    <!--HistorialTransacciones-->
    <HistorialTransaccionesApp :transacciones="transacciones" @eliminar-transaccion="eliminarTransaccion"/>
    <!--/HistorialTransacciones-->
    <!--AgregarTransaccion-->
    <AgregarTransaccionApp @agregar-transaccion="agregarTransaccion"/>
    <!--/AgregarTransaccion-->
  </div>
</template>

<style scoped></style>
