<script setup>
    const props = defineProps({
        type: String,
        index: Number
    })
    const emit = defineEmits(['toggleInput'])

    const toggleInput = () => {
        emit('toggleInput')
    }

</script>

<template>
    <button @click="toggleInput">{{ props.type.toUpperCase() }}</button>
</template>