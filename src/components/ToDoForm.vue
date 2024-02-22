<template>
  <form>
    <label for="new-todo-input"> What needs to be done? </label>
    <input
      type="text"
      id="new-todo-input"
      name="new-todo"
      autocomplete="off" 
      v-model="label"
      class="input__lg" 
    />

    <button @click.prevent="submit" class="btn btn__primary btn__lg">Add</button>
  </form>

</template>

<script setup>
const emit = defineEmits(['todo-added'])
import {ref} from 'vue'

const label = ref("")


function submit() {
    if (label.value == "") {
        return 
    }
    emit("todo-added", label.value);
    label.value = ""
}
</script>