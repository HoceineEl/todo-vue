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
          <li class="mb-2">
            Creating a new todo is a breeze. Just find the input field at the
            top of the page.
          </li>
          <li class="mb-2">Type in the task you want to add to your list.</li>
          <li class="mb-2">
            Click the "Create" button, and your new task will instantly appear
            in your list.
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
