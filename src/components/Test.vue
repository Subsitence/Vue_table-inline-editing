<script setup>
    import { ref, onMounted, computed, reactive } from 'vue'
    import Child from './Child.vue'

    const count = ref(0)
    let rawHtml = 'RAW HTML'
    let isDisabled = false
    const state = reactive({ count: 0 })
    const message = ref('')
    const items = reactive([
        {
            name: 'hai anh',
            age: 18
        },
        {
            name: 'duy thai',
            age: 21
        },
        {
            name: 'van nam',
            age: 20
        },
        {
            name: 'thai dui',
            age: 19
        }
    ])
    const now = computed(() => new Date())

    const changeDisabled = () => {
        isDisabled = !isDisabled
    }

    const increment = () => {
        count.value++
        state.count++
        changeDisabled()
    }

    const getMe = (name) => {
        return name
    }

    onMounted(() => {
        console.log('component mounted')
    })
</script>

<template>
    <h1>Hello world!</h1>
    <button @click="increment()">Count is: {{ count }} and count 2 is {{ state.count }}</button>
    <h1>{{ getMe(`${count}`) }}</h1>
    <p>Using v-html directive: <span v-html="now"></span></p>
    <ul>
        <template v-for="({ name, age }, index) in items">
            <li v-if="age > 18">{{ index }} - {{ name }} is {{ age }} years old</li>
        </template>
    </ul>

    <p>This is something: {{ message }}</p>
    <input v-model="message" placeholder="type something"/>
    
    <Child :title="'dm vdnh'" :number="14"/>
</template>

<style scoped>
    #testId {
        color: red;
    }
</style>