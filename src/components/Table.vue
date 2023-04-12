<script setup>
    import Row from './Row.vue'
    import { ref, reactive } from 'vue';
    const data = reactive([
        {
            name: 'hai anh 1',
            age: 18,
            country: 'Viet Nam'
        },
        {
            name: 'hai anh 2',
            age: 19,
            country: 'Viet Nam'
        },
        {
            name: 'hai anh 3',
            age: 20,
            country: 'Viet Nam'
        },
    ])

    const editOffset = ref(-1)

    const changeOffset = (newOffset) => {
        editOffset.value = newOffset
    }

    const update = (payload) => {
        data[payload.index].name = payload.name 
        data[payload.index].age = payload.age 
        data[payload.index].country = payload.country
    }
    
    const deleteRow = (index) => {
        data.splice(index, 1)
    }
    
</script>

<template>
    <table>
        <tr>
            <th>Name</th>
            <th>Age</th>
            <th>Country</th>
            <th>Edit</th>
        </tr>
        <tr v-for="(person, index) in data">
            <Row 
                v-bind="person" 
                :index="index"
                :editOffset="editOffset"
                @changeOffset="changeOffset($event)"
                @update="update($event)"
                @delete="deleteRow($event)"
            />
        </tr>
    </table>
</template>

<style scoped>
    table {
        font-family: arial, sans-serif;
        border-collapse: collapse;
        width: 100%;
    }

    td, th {
        border: 1px solid #dddddd;
        text-align: left;
        padding: 8px;
    }

    tr:nth-child(even) {
        background-color: #dddddd;
    }
</style>