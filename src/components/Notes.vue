<template>
  <div
    class="grid gap-5 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 mt-6 mb-6 container mx-auto"
  >
    <Note
      v-for="(note, index) in notes"
      :key="index"
      :note="note"
      @deleted="refresh"
    />
    <NoteAdd />
  </div>
  <NotesForm v-if="show" @added="refresh" @saved="refresh" />
</template>

<script setup>
import { onMounted } from 'vue'
import { show, notes, getAll } from '~/helpers/useNotes'

onMounted(() => refresh())

const refresh = async () => await getAll()
</script>
