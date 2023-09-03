<script setup>
import { Icon } from "@iconify/vue";
const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
  index: {
    type: Number,
    required: true,
  },
});

defineEmits([
  "edit-todo",
  "delete-todo",
  "toggle-complete",
  "complete-editing",
  "update-todo",
]);
</script>

<template>
  <li
    class="flex flex-col md:flex-row w-[90%] md:w-[35rem] items-center relative rounded-md p-4 bg-gradient-to-r from-purple-400 to-indigo-300 gap-5 hover:shadow-lg group hover:shadow-gray-300 mb-4 transition-all duration-500 hover:scale-[1.008]"
  >
    <div>
      <input
        type="checkbox"
        @input="$emit('toggle-complete', index)"
        :checked="todo.isComplete"
        class="rounded-full appearance-none w-6 h-6 shadow-md shadow-gray-600 checked:bg-orange-300 bg-slate-100"
      />
    </div>
    <div class="w-full">
      <textarea
        type="text"
        v-if="todo.isEditing"
        @input="$emit('update-todo', $event.target.value, index)"
        class="rounded-lg px-3 py-1 text-gray-600 focus:outline-none w-full"
        :value="todo.todo"
        style="resize: none"
        rows="10"
        placeholder="Edit your task here..."
        aria-label="Edit task"
      ></textarea>
      <p
        v-else
        class="text-gray-200 font-semibold pe-9 text-justify break-words"
        :class="{ 'line-through': todo.isComplete }"
        aria-label="Task description"
      >
        {{ todo.todo }}
      </p>
    </div>
    <div
      class="flex gap-3 mt-2 md:mt-0 relative right-3 group-hover:opacity-100 opacity-0 transition duration-500"
    >
      <Icon
        icon="ph:pen-fill"
        @click="$emit('edit-todo', index)"
        class="cursor-pointer"
        :key="todo.id"
        v-if="!todo.isEditing"
        color="white"
        width="25"
        aria-label="Edit task"
      />
      <Icon
        icon="ph:check-circle"
        class="cursor-pointer"
        color="#8b5cf6"
        width="25"
        v-else
        @click="$emit('complete-editing', index)"
        aria-label="Save changes"
      />
      <Icon
        icon="ph:trash"
        class="cursor-pointer"
        color="#F87171"
        :key="todo.id"
        @click="$emit('delete-todo', index)"
        width="25"
        aria-label="Delete task"
      />
    </div>
  </li>
</template>

<style lang="scss" scoped></style>
