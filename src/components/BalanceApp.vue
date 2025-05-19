<script setup lang="ts">

type PropTypes = {
    total: number
}

defineProps<PropTypes>();

</script>
<template>
    <div class="col-4">
        <h2>Tu balance:</h2>

        <h3 class="text-end">{{ total.toFixed(2) }}</h3>
    </div>
</template>