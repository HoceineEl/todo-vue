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
    class="flex w-[30rem] items-center relative rounded-md p-4 bg-gray-200 gap-5 hover:shadow-lg group hover:shadow-gray-300 mb-4 mx-10 transition-all duration-500 hover:scale-[1.02]"
  >
    <input
      type="checkbox"
      @input="$emit('toggle-complete', index)"
      :checked="todo.isComplete"
      class="rounded-full appearance-none w-6 h-6 shadow-md shadow-gray-600 checked:bg-purple-500 bg-slate-100"
    />
    <div class="">
      <input
        type="text"
        v-if="todo.isEditing"
        @input="$emit('update-todo', $event.target.value, index)"
        class="rounded-lg px-3 object-fill text-gray-600"
        :value="todo.todo"
      />
      <span
        v-else
        class="text-gray-700 pe-9"
        :class="{ 'line-through': todo.isComplete }"
        >{{ todo.todo }}</span
      >
    </div>
    <div
      class="flex gap-3 absolute right-3 group-hover:opacity-100 opacity-0 transition duration-500"
    >
      <Icon
        icon="ph:pen-fill"
        @click="$emit('edit-todo', index)"
        class="cursor-pointer"
        :key="todo.id"
        v-if="!todo.isEditing"
        color="#34D399"
        width="25"
      />
      <Icon
        icon="ph:check-circle"
        class="cursor-pointer"
        color="#8b5cf6"
        width="25"
        v-else
        @click="$emit('complete-editing', index)"
      />
      <Icon
        icon="ph:trash"
        class="cursor-pointer"
        color="#F87171"
        :key="todo.id"
        @click="$emit('delete-todo', index)"
        width="25"
      />
    </div>
  </li>
</template>

<style lang="scss" scoped></style>
