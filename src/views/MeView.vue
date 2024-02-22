<template>
    <div>
        <to-do-form @todo-added="addToDo"></to-do-form>
        <ul aria-labelledby="list-summary" class="stack-large">
            <li v-for="item in ToDoItems" :key="item.id">
                <to-do-item 
                    :label="item.label" 
                    :done="item.done"
                    :id="item.id"></to-do-item>
            </li>
        </ul>
    </div>
</template>

<script setup>
    import ToDoItem from '../components/ToDoItem.vue'
    import ToDoForm from "../components/ToDoForm.vue";

    import {reactive} from 'vue'
    import _ from 'lodash'

    const ToDoItems = reactive([
        {id: _.uniqueId('todo-'), label: "Learn Vue", done: true},
        {id: _.uniqueId('todo-'), label: "Create a Vue project with the CLI", done: true },
        {id: _.uniqueId('todo-'), label: "Have fun", done: true },
        {id: _.uniqueId('todo-'), label: "Create a to-do list", done: false },
    ])
    function addToDo(toDoLabel){
        ToDoItems.push({id:_.uniqueId('todo-'), label: toDoLabel, done: false});
        console.log(ToDoItems)

    }




</script>

