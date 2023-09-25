
<script setup>
    defineProps({
        title: {
            type: String,
            default: 'Click me'
        },
        id: Number,
        body: {
            type: String,
            required: true
        },
    })
    const emit = defineEmits(['handleClickButton'])
    
</script>

<template>
    <div class="border my-3 p-4 rounded-2" :id="id">
        <h2>{{ title }}</h2>
        <p>{{ body }}</p>
        <button class="btn btn-primary" @click="emit('handleClickButton', id)">Click me</button>
    </div>
</template>
