<script setup>
import { RouterLink } from "vue-router";
</script>
<template>
  <header class="bg-gradient-to-r from-purple-950 to-purple-400">
    <nav class="flex container justify-between items-center mx-auto">
      <img class="w-32" src="../assets/imgs/todo-logo.png" />
      <ul class="flex gap-10 font-semibold text-indigo-50 mr-8">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped></style>
