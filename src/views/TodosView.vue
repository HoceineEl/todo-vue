<script setup>
  import TodoCreator from "../components/TodoCreator.vue";
  import {
    computed,
    ref,
    watch
  } from "vue";
  import {
    uid
  } from "uid";
  import TodoItem from "../components/TodoItem.vue";
  import {
    Icon
  } from "@iconify/vue";
  import 
    Draggable
   from "vuedraggable";
  let todoList = ref([]);
  watch(
    todoList,
    () => {
      localStorage.setItem("todoList", JSON.stringify(todoList.value));
    }, {
      deep: true,
    }
  );
  const todosCompleted = computed(() => {
    return todoList.value.every((todo) => todo.isComplete)
  })
  console.log(todosCompleted)
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
    })
  };
  const deleteTodo = (index) => {
    todoList.value.splice(index, 1)
  };
  const editTodo = (index) => {
    todoList.value[index].isEditing = true
  };
  const onToggleComplete = (index) => {
    todoList.value[index].isComplete = !todoList.value[index].isComplete
  };
  const onCompleteEditing = (index) => {
    todoList.value[index].isEditing = false
  };
  const onUpdateTodo = (value, index) => {
    todoList.value[index].todo = value
  };
</script>

<template>
  <h2 class="text-3xl text-center  mt-20 font-bold text-gray-200">
    Create Todo
  </h2>
  <TodoCreator @form-submitted="addTodo" />
  <p class="flex gap-4 justify-center" v-if="todoList.length==0">
    <Icon icon="noto-v1:sad-but-relieved-face" width="20"></Icon>
    <p class="text-sm text-gray-200 ">You have no todo's to complete ! Add one!</p>
  </p>
  <Draggable  class="flex items-center flex-col"  
   v-model="todoList" 
   tag="ul"
   drag-class="drag"
   ghost-class="ghost"
   >
   <template #item="{ element: todo,index }">
     <TodoItem
       @edit-todo="editTodo"
       @delete-todo="deleteTodo"
       @toggle-complete="onToggleComplete"
       @complete-editing="onCompleteEditing"
       @update-todo="onUpdateTodo"
       :key="todo.id"
       :todo="todo"
       :index="index"
     ></TodoItem>
   </template>
 </Draggable>


  <p class="flex gap-4 justify-center m-4 transition-all duration-1000  " v-show="todosCompleted && todoList.length>0">
    <Icon icon="noto-v1:party-popper" width="20"></Icon>
    <p class="text-sm text-gray-600">You have complete all your tasks!</p>
  </p>
</template>
<style>
.drag .drag-div {
  transform: rotate(10deg) !important;
}
.ghost {
  background-color: aliceblue;
}
.ghost input , .ghost p ,.ghost div.ms-3{
  visibility: hidden;
  transition: 1s;
}

</style>