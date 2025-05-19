<script setup lang="ts">
type PropTypes={
  ingresos: number;
  gastos: number;
}

defineProps<PropTypes>();

</script>
<template>
    <div class="row row-cols-1 row-cols-md-2 g-4 mt-3">
      <div class="col">
        <div class="card border-success">
          <div class="card-header text-bg-success">
            <h3 class="card-title text-center">
              <i class="fa-solid fa-sack-dollar"></i>&nbsp;Entradas
            </h3>
          </div>
          <div class="card-body">
            <p class="card-text h2 text-center text-success">+ ${{ ingresos.toFixed(2) }}</p>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card border-danger">
          <div class="card-header text-bg-danger">
            <h3 class="card-title text-center"><i class="fa-solid fa-money-bill-trend-up text-white"></i>&nbsp;Salidas
            </h3>
          </div>
          <div class="card-body">
            <p class="card-text h2 text-center text-danger"> ${{ gastos.toFixed(2) }}</p>
          </div>
        </div>
      </div>
    </div>
</template>