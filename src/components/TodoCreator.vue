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
  // setTimeout(() => {
  //   todo.errMsg = "";
  //   todo.invalid = null;
  // }, 3000);
  todo.invalid = true;
  todo.errMsg = "Cannot set an empty string";
};
</script>
<template>
  <div class="container flex justify-center mx-auto">
    <div
      class="w-fit h-10 my-4 focus-within:shadow-lg focus-within:shadow-purple-200"
    >
      <input
        type="text"
        class="w-[28rem] rounded-ss-md h-10 text-gray-400 focus:outline-none px-3 border-2 border-purple-300 border-r-0"
        :class="{ 'border-red-400': todo.invalid }"
        v-model="todo.content"
        id=""
      />
      <button
        @click="onSubmit()"
        class="h-10 px-3 bg-purple-300 border-none rounded-ee-md text-white font-semibold"
      >
        Create
      </button>
    </div>
    <p v-if="todo.invalid" class="text-sm -mt-1 text-purple-300">
      {{ todo.errMsg }}
    </p>
  </div>
</template>

<style lang="scss" scoped></style>
