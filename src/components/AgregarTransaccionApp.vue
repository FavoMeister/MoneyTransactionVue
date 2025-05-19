<template>
    <div class="row mt-3">
      <div class="col">
        <h2 class="border-bottom border-primary pb-2">
          <i class="fa-regular fa-calendar-plus"></i>&nbsp;Agregar transacción
        </h2>
        <form>
          <div class="mb-3">
            <label for="concepto" class="form-label">Concepto</label>
            <input type="text" class="form-control" id="concepto" aria-describedby="conceptoHelp" />
          </div>
          <div class="mb-3">
            <label for="cantidad" class="form-label">Cantidad</label>
            <input type="text" class="form-control" id="cantidad" aria-describedby="cantidadHelp" />
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