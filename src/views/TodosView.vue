<script setup>
import TodoCreator from "../components/TodoCreator.vue";
import { ref } from "vue";
import { uid } from "uid";
let todoList = ref([]);

const addTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isComplete: null,
    isEditing: null,
  });
};
</script>

<template>
  <h2
    class="text-3xl text-center mt-20 font-bold bg-gradient-to-b text-transparent from-purple-900 to-orange-200 bg-clip-text"
  >
    Create Todo
  </h2>
  <TodoCreator @form-submitted="addTodo" />
</template>
