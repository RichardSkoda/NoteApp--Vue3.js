<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup

import { ref } from 'vue';
import NoteCard from './components/NoteCard.vue';
import NotesModal from './components/NotesModal.vue';
import DeleteModal from './components/DeleteModal.vue';


const showModal = ref(false);
const showDeleteModal = ref(false);

const openAddNoteModal = () => {
    showModal.value = true;
}

// change showModal value to false after close modal
const updateShowModal = (e: boolean) => {
  showModal.value = e
}

const openDeleteModal = () => {
  showDeleteModal.value = true;
}

const updateDeleteModal = (e: boolean) => {
  showDeleteModal.value = e
}



</script>

<template>
  <div class="note-container">
    <NoteCard 
      @showdeletemodal="openDeleteModal"
      />
    <a class="plus-card" @click="openAddNoteModal">
        <font-awesome-icon icon="fa-solid fa-circle-plus" class="plus-icon" />
    </a>
    <NotesModal 
      :open-modal="showModal"
      @showmodal="updateShowModal"
    />
    <DeleteModal 
      :open-modal="showDeleteModal"
      @showdeletemodal="updateDeleteModal"/>
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

/* add button style */
.plus-card {
        border: solid 2px #71717a;
        border-radius: 1%;
        background-color: #0f0f0f;
        color: white;
        cursor: pointer;
        opacity: 0.5;
        transition: all 0.2s ease;
        margin: 10%;
    }

    .plus-card:hover {
        opacity: 1;
        margin: 0;
    }

    .plus-icon {
        position: relative;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        color: white;
        font-size: 50px;
}

</style>