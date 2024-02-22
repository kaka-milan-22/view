<template>
    <div>
      <input type="checkbox" id="todo-item" :checked="isDone" />
      <label :for="id">{{ label }}</label>
    </div>
</template>

<script setup>
    import _ from 'lodash'

    import {ref} from 'vue'
    const props = defineProps({
        label: {required: true, type: String},
        done: {default: false, type: Boolean},
        id: {required: true, type: String}
    })

</script>