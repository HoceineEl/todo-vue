<script setup></script>

<template>
  <main class="bg-gray-100 min-h-screen flex items-center justify-center">
    <div class="max-w-2xl w-full bg-white p-8 rounded-lg shadow-lg">
      <h1 class="text-3xl font-semibold mb-4 text-purple-600">
        Vue.js Todo App
      </h1>

      <div class="mb-6">
        <h2 class="text-xl font-semibold mb-2">About</h2>
        <p class="text-gray-700">
          Welcome to the Vue.js Todo App! This modern and efficient application
          helps you manage your tasks with ease. It features a sleek and
          intuitive interface designed with Vue.js and styled in shades of
          <span class="text-purple-600">purple</span> using Tailwind CSS.
        </p>
      </div>

      <div class="mb-6">
        <h2 class="text-xl font-semibold mb-2">How to Use</h2>
        <ol class="list-decimal pl-6 text-gray-700">
          <!-- Existing How to Use steps -->
          <!-- ... -->

          <!-- New Drag and Drop Instruction -->
          <li class="mb-2">
            To rearrange your tasks, you can now use
            <span class="font-bold text-purple-600">drag-and-drop</span>
            ! Simply click and hold on a task, then drag it to your desired
            position within the list.
          </li>
        </ol>
      </div>

      <div class="mb-6">
        <h2 class="text-xl font-semibold mb-2">Editing a Todo</h2>
        <ol class="list-decimal pl-6 text-gray-700">
          <li class="mb-2">
            To edit a todo, simply click on the
            <span class="text-purple-600">Edit</span> icon (pencil) located next
            to the task you want to modify.
          </li>
          <li class="mb-2">
            The task text will become editable. Edit the task text as needed.
          </li>
          <li class="mb-2">
            Click the <span class="text-purple-600">Check</span> icon to save
            your changes.
          </li>
        </ol>
      </div>

      <div class="mb-6">
        <h2 class="text-xl font-semibold mb-2">Completing a Todo</h2>
        <ol class="list-decimal pl-6 text-gray-700">
          <li class="mb-2">
            To mark a todo as complete, simply check the checkbox next to the
            task.
          </li>
          <li class="mb-2">
            The task text will be crossed out to indicate that it's completed.
          </li>
        </ol>
      </div>
    </div>
  </main>
</template>
