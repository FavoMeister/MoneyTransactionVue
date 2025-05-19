<script setup lang="ts">

type PropTypes = {
    totalTransacciones: number
}

defineProps<PropTypes>();

</script>
<template>
    <div class="col-8">
        <h2 class="text-end"># Transacciones:</h2>
        <h3 class="text-end">{{ totalTransacciones }}</h3>
    </div>
</template>