<script setup lang="ts">
import EncabezadoApp from './EncabezadoApp.vue';
import BalanceApp from './BalanceApp.vue';
import NumeroTransaccionesApp from './NumeroTransaccionesApp.vue';
import ResumenApp from './ResumenApp.vue';
import HistorialTransaccionesApp from './HistorialTransaccionesApp.vue';
import AgregarTransaccionApp from './AgregarTransaccionApp.vue';
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
    <HistorialTransaccionesApp/>
    <!--/HistorialTransacciones-->
    <!--AgregarTransaccion-->
    <AgregarTransaccionApp/>
    <!--/AgregarTransaccion-->
  </div>
</template>

<style scoped></style>
