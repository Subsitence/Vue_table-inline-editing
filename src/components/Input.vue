<script setup>
    import { onMounted, ref } from 'vue';
    const props = defineProps({
        value: [String, Number]
    })
    const emit = defineEmits(['updateCell'])
    const updateInput = (value) => {
        emit('updateCell', value)
    }
</script>


<template>
    <input :value="props.value" @change="updateInput($event.target.value)"/>
</template>