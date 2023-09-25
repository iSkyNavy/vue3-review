<script setup>
    defineProps(["disabledPrev", "disabledNext"]);
    const emit = defineEmits(["handlePagination"]);
</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button type="button" :class="`btn btn-outline-success`" @click="emit('handlePagination', 'prev')" :disabled="disabledPrev">Preview</button>
        <button type="button" class="btn btn-outline-primary" @click="emit('handlePagination', 'next')" :disabled="disabledNext">Next</button>
    </div>
</template>

<style>

</style>