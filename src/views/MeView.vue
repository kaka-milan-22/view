<template>
    <div>
        <h2 id="list-summary">{{listSummary}}</h2>
        <to-do-form @todo-added="addToDo"></to-do-form>
        <ul aria-labelledby="list-summary" class="stack-large">
            <li v-for="item in ToDoItems" :key="item.id">
                <to-do-item 
                    :label="item.label" 
                    :done="item.done"
                    :id="item.id"
                    @checkbox-changed="updateDoneStatus(item.id)"/>
            </li>
        </ul>
    </div>
</template>

<script setup>
    import ToDoItem from '../components/ToDoItem.vue'
    import ToDoForm from "../components/ToDoForm.vue";

    import {reactive, computed} from 'vue'
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

    function updateDoneStatus(toDoId) {
        const toDoToUpdate = ToDoItems.find((item) => item.id === toDoId)
        toDoToUpdate.done = !toDoToUpdate.done
    }

    const listSummary = computed(() => {
        const numberFinishedItems = ToDoItems.filter((item) =>item.done).length
        return `${numberFinishedItems} out of ${ToDoItems.length} items completed`
    })



</script>

