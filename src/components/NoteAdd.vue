<template>
  <div
    class="bg-black text-pink-500 rounded space-y-2 flex justify-center items-center"
  >
    <button
      @click="showToggle"
      class="opacity-70 transform transition-all hover:scale-105 hover:opacity-80"
    >
      <ic:outline-add-box class="w-36 h-36" />
    </button>
  </div>
</template>

<script setup>
import { showToggle } from '~/helpers/useNotes'
</script>
