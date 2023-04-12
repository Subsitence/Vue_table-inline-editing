<script setup>
    import { onMounted } from 'vue';

    const props = defineProps({
        title: String,
        number: Number
    })

    onMounted(() => {
        console.log(props)
        console.log('hello world')
    })

</script>

<template>
    <h1>{{ props.title }} - {{ props.number }}</h1>
</template>