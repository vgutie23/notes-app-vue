<template>
  <div
    class="absolute inset-0 w-screen h-screen bg-gray-900 bg-opacity-95 flex justify-center items-center"
  >
    <button @click="reset" class="text-gray-100 absolute top-2 right-2">
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
          class="rounded py-2 px-4 bg-gray-100"
          placeholder="New Note Title"
          v-model="newNote.title"
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
          class="rounded py-2 px-4 bg-gray-100"
          placeholder="New Note Content"
          v-model="newNote.content"
        />
      </div>
      <div>
        <button
          v-if="noteToEdit"
          @click="saveNote"
          class="w-full bg-pink-500 bg-opacity-95 text-gray-100 text-lg font-semibold p-2 rounded mt-3 hover:bg-pink-900 hover:text-pink-200"
        >
          Save Note
        </button>
        <button
          v-else
          @click="addNote"
          class="w-full bg-indigo-700 bg-opacity-95 text-gray-100 text-lg font-semibold p-2 rounded mt-3 hover:bg-indigo-900 hover:text-indigo-200"
        >
          Add Note
        </button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { reactive, defineEmit, onMounted } from 'vue'
import { showToggle, add, noteToEdit, save } from '~/helpers/useNotes'

const newNote = reactive({
  title: '',
  content: '',
})

onMounted(() => {
  if (noteToEdit.value) {
    newNote.title = noteToEdit.value.title
    newNote.content = noteToEdit.value.content
  }
})

const emit = defineEmit(['added', 'saved'])

const reset = event => {
  showToggle()
  newNote.title = ''
  newNote.content = ''
  noteToEdit.value = null
  emit(event)
}

const addNote = async () => {
  await add(newNote)
  reset('added')
}

const saveNote = async () => {
  await save({ id: noteToEdit.value.id, ...newNote })
  reset('saved')
}
</script>
