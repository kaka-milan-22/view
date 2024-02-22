<template>
    <ul>
    <li v-for="item in ToDoItems" :key="item.id">
        <to-do-item 
            :label="item.label" 
            :done="item.done"
            :id="item.id"></to-do-item>
    </li>
    </ul>
</template>

<script setup>
import ToDoItem from '../components/ToDoItem.vue'
import {ref} from 'vue'
import _ from 'lodash'

const ToDoItems = ref([
    {id: _.uniqueId('todo-'), label: "Learn Vue", done: false},
    {id: _.uniqueId('todo-'), label: "Create a Vue project with the CLI", done: true },
    {id: _.uniqueId('todo-'), label: "Have fun", done: true },
    {id: _.uniqueId('todo-'), label: "Create a to-do list", done: false },
])
</script>