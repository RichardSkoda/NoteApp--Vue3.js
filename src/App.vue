<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup

import NoteCard from './components/NoteCard.vue';
import AddNoteCard from './components/AddNoteCard.vue';
import NotesModal from './components/NotesModal.vue';

</script>

<template>
  <div class="note-container">
    <NoteCard/>
    <NoteCard/>
    <NoteCard/>
    <NoteCard/>
    <AddNoteCard/>
    <NotesModal/>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

* {
  font-family: 'Roboto', sans-serif;
  margin: 0;
  padding: 0;
}

body {
  /* margin: 1%; */
  background-color: #0f0f0f
}

.note-container {
  min-height: 100vh;
  background-color: #0f0f0f;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  column-gap: 0.5rem;
  grid-gap: 0.5rem;
  padding: 1%;
}

</style>