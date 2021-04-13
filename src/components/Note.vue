<template>
  <div
    class="bg-black text-pink-500 text-opacity-90 rounded text-center p-2 space-y-2"
  >
    <h1 class="text-3xl font-bold tracking-wide">Note Title</h1>
    <p class="text-base font-medium text-indigo-500 text-opacity-90">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Dignissimos,
      beatae excepturi ut nisi, quibusdam, rerum aliquam reprehenderit inventore
      itaque voluptates odio soluta amet dolore accusamus debitis voluptas ullam
      ipsa quisquam?
    </p>
    <div class="flex justify-end space-x-2">
      <button class="hover:text-yellow-400 hover:text-opacity-80">
        <uil:file-edit-alt />
      </button>
      <button class="hover:text-red-600 hover:text-opacity-90">
        <octicon:trash-24 />
      </button>
    </div>
  </div>
</template>
