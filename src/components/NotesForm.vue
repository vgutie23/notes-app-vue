<template>
  <div
    class="absolute inset-0 w-screen h-screen bg-indigo-800 bg-opacity-95 flex justify-center items-center"
  >
    <button @click="showToggle" class="text-gray-200 absolute top-2 right-2">
      <ant-design:close-circle-twotone class="text-5xl" />
    </button>
    <form @submit.prevent class="space-y-4">
      <div class="flex flex-col">
        <label
          for="title"
          class="text-pink-500 text-opacity-90 text-xl font-semibold tracking-widest mb-2"
          >Note Title</label
        >
        <input
          type="text"
          name="title"
          class="rounded py-2 px-4"
          placeholder="New Note Title"
        />
      </div>
      <div class="flex flex-col">
        <label
          for="content"
          class="text-pink-500 text-opacity-90 text-xl font-semibold tracking-widest mb-2"
          >Note Content</label
        >
        <textarea
          name="content"
          class="rounded py-2 px-4"
          placeholder="New Note Content"
        />
      </div>
      <div>
        <button
          class="w-full bg-pink-500 bg-opacity-90 text-gray-100 text-lg font-semibold p-2 rounded mt-3 hover:bg-pink-600 hover:text-pink-900"
        >
          Add Note
        </button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { showToggle } from '~/helpers/useNotes'
</script>
