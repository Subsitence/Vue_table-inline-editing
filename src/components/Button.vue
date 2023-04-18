<script setup>
    const props = defineProps({
        type: String,
        index: Number
    })
    const emit = defineEmits(['handleEvent'])

    const handleEvent = () => {
        emit('handleEvent')
    }

</script>

<template>
    <button @click="handleEvent">{{ props.type.toUpperCase() }}</button>
</template>