<script setup>
import TodoCreator from "../components/TodoCreator.vue";
import { ref } from "vue";
import { uid } from "uid";
import TodoItem from "../components/TodoItem.vue";
let todoList = ref([]);
const setTodoListToLocalStorage = () => {
  localStorage.setItem("todoList", JSON.stringify(todoList.value));
};
const fetchTodoList = () => {
  const todoValue = JSON.parse(localStorage.getItem("todoList"));
  if (todoValue) {
    todoList.value = todoValue;
  }
};
fetchTodoList();
const addTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isComplete: false,
    isEditing: false,
  });
  setTodoListToLocalStorage();
};
const deleteTodo = (index) => {
  todoList.value.splice(index, 1);
  setTodoListToLocalStorage();
};
const editTodo = (index) => {
  todoList.value[index].isEditing = true;
  setTodoListToLocalStorage();
};
const onToggleComplete = (index) => {
  todoList.value[index].isComplete = !todoList.value[index].isComplete;
  setTodoListToLocalStorage();
};
const onCompleteEditing = (index) => {
  todoList.value[index].isEditing = false;
  setTodoListToLocalStorage();
};
const onUpdateTodo = (value, index) => {
  todoList.value[index].todo = value;
  setTodoListToLocalStorage();
};
</script>

<template>
  <h2 class="text-3xl text-center mt-20 font-bold text-gray-700">
    Create Todo
  </h2>
  <TodoCreator @form-submitted="addTodo" />
  <ul class="text-center flex items-center flex-col">
    <TodoItem
      v-for="(todo, index) in todoList"
      @edit-todo="editTodo"
      @delete-todo="deleteTodo"
      @toggle-complete="onToggleComplete"
      @complete-editing="onCompleteEditing"
      @update-todo="onUpdateTodo"
      :key="todo.id"
      :todo="todo"
      :index="index"
    ></TodoItem>
  </ul>
</template>
