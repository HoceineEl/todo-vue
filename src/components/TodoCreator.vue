<script setup>
import { ref, defineEmits, reactive } from "vue";
const todo = reactive({
  content: "",
  invalid: null,
  errMsg: "",
});
const emit = defineEmits(["form-submitted"]);
const onSubmit = () => {
  todo.invalid = null;
  if (todo.content != "") {
    emit("form-submitted", todo.content);
    todo.content = "";
    return;
  }
  setTimeout(() => {
    todo.errMsg = "";
    todo.invalid = null;
  }, 3000);
  todo.invalid = true;
  todo.errMsg = "Cannot set an empty string";
};
</script>
<template>
  <div class="container flex items-center flex-col mx-auto">
    <div class="overflow-hidden rounded-md w-fit my-4">
      <input
        type="text"
        class="w-80 h-8 focus:outline-none px-3 border-2 border-orange-300 border-r-0"
        v-model="todo.content"
        id=""
      />
      <button
        @click="onSubmit()"
        class="h-8 px-3 bg-orange-300 border-none text-white font-semibold"
      >
        Create
      </button>
    </div>
    <p v-if="todo.invalid" class="text-sm -ms-56 -mt-3 text-red-500">
      {{ todo.errMsg }}
    </p>
  </div>
</template>

<style lang="scss" scoped></style>
