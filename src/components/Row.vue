<script setup>
    import Cell from './Cell.vue'
    import Button from './Button.vue'
    import { ref, computed } from 'vue';
    const person = defineProps({
        name: String,
        age: [Number, String],
        country: String,
        index: Number,
        editOffset: Number
    })
    const emit = defineEmits(['changeOffset', 'update', 'delete'])

    const isShowInput = computed(() => {
        return person.index === person.editOffset
    })

    const startEditing = () => {
        emit('changeOffset', person.index)
    }

    const cancelEditing = () => {
        emit('changeOffset', -1)
    }

    const rowData = {
        name: person.name,
        age: person.age,
        country: person.country,
        index: person.index
    }

    const updateRow = (payload) => {
        rowData[payload.category] = payload.value
    }
    const submitUpdate = () => {
        emit('update', rowData)
        cancelEditing()
    }

    const deleteRow = () => {
        emit('delete', person.index)
    }
</script>

<template>
    <Cell @updateRow="updateRow($event)" v-bind="{ value: person.name, isShow: isShowInput, category: 'name'}"/>
    <Cell @updateRow="updateRow($event)" v-bind="{ value: person.age, isShow: isShowInput, category: 'age'}"/>
    <Cell @updateRow="updateRow($event)" v-bind="{ value: person.country, isShow: isShowInput, category: 'country'}"/>
    <td>
        <Button 
            :index="person.index"
            :type="'edit'"
            @toggleInput="startEditing"
            v-show="!isShowInput"
        />
        <Button 
            :type="'delete'" 
            v-show="!isShowInput"
            @click="deleteRow"
        />
        <Button 
            :type="'update'" 
            v-show="isShowInput"
            @toggleInput="submitUpdate"
        />
        <Button 
            :type="'cancel'" 
            v-show="isShowInput" 
            @toggleInput="cancelEditing"
        />
    </td>
</template>