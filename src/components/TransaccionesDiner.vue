<script setup lang="ts">
import EncabezadoApp from './EncabezadoApp.vue';
import BalanceApp from './BalanceApp.vue';
import NumeroTransaccionesApp from './NumeroTransaccionesApp.vue';
import ResumenApp from './ResumenApp.vue';
import HistorialTransaccionesApp from './HistorialTransaccionesApp.vue';
import AgregarTransaccionApp from './AgregarTransaccionApp.vue';

import { ref } from 'vue';
import type { Transaccion } from '@/types/types';

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

</script>

<template>
<div class="container">
  <!--Encabezado-->
    <EncabezadoApp/>
    <!--/Encabezado-->
    <div class="row mt-3">
      <!--Balance-->
      <BalanceApp/>
      <!--/Balance-->
      <!--NumeroTransacciones-->
      <NumeroTransaccionesApp/>
      <!--/NumeroTransacciones-->
    </div>
    <div class="border-bottom border-primary">
    </div>
    <!--Resumen-->
    <ResumenApp/>
    <!--/Resumen-->
    <!--HistorialTransacciones-->
    <HistorialTransaccionesApp :transacciones="transacciones"/>
    <!--/HistorialTransacciones-->
    <!--AgregarTransaccion-->
    <AgregarTransaccionApp/>
    <!--/AgregarTransaccion-->
  </div>
</template>

<style scoped></style>
