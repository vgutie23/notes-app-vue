<template>
  <div
    class="grid gap-5 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 mt-6 mb-6 container mx-auto"
  >
    <Note v-for="n in 10" :key="n" />
    <NoteAdd />
  </div>
  <NotesForm v-if="show" />
</template>

<script setup>
import { show } from '~/helpers/useNotes'
</script>
