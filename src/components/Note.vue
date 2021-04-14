<template>
  <div
    class="bg-black text-pink-500 text-opacity-90 rounded text-center p-2 space-y-2"
  >
    <h1 class="text-3xl font-bold tracking-wide">{{ $props.note.title }}</h1>
    <p class="text-base font-medium text-indigo-500 text-opacity-90">
      {{ $props.note.content }}
    </p>
    <div class="flex justify-end space-x-2">
      <button
        @click="editNote(note)"
        class="hover:text-yellow-400 hover:text-opacity-80"
      >
        <uil:file-edit-alt />
      </button>
      <button
        @click="removeNote($props.note.id)"
        class="hover:text-red-600 hover:text-opacity-90"
      >
        <octicon:trash-24 />
      </button>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmit } from 'vue'
import { remove, showToggle, noteToEdit } from '~/helpers/useNotes'

defineProps({
  note: Object,
  default: {
    id: 0,
    title: '',
    content: '',
  },
})

const emit = defineEmit(['deleted'])

const removeNote = async id => {
  await remove(id)
  emit('deleted')
}

const editNote = note => {
  noteToEdit.value = note
  showToggle()
}
</script>
