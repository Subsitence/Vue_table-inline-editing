<script setup>
    import Input from './Input.vue'
    import { ref, nextTick, reactive } from 'vue'

    const data = defineProps({
        value: [String, Number],
        isShow: Boolean,
        category: String
    })
    const emit = defineEmits(['updateRow'])

    const updateCell = (value) => {
        emit('updateRow', {
            category: data.category,
            value
        })
    }

</script>

<template>
    <td>
        <p v-show="!isShow">{{ data.value }}</p>
        <Input
            v-show="isShow"
            :value="data.value"
            @updateCell="updateCell($event)"
        />
    </td>
</template>