<template>
    <div>
        <button class="open-button" @click="openModal">
            Press me!
        </button>
    </div>
    <TransitionRoot appear :show="isOpen" as="template">
      <Dialog as="div" @close="closeModal" class="modal-dialog">
        <TransitionChild
          class="overlay-transition"
        >
            <div class="modal-overlay"></div>
        </TransitionChild>

        <div class="modal-container">
            <div class="modal">
                <TransitionChild
                class="modal-transition"
                >
                <DialogPanel
                    class="dialog-panel"
                >
                    <DialogTitle
                    as="h3"
                    class="modal-title"
                    >
                    Note Detail
                    </DialogTitle>
                    <div class="modal-info-container">
                        <div class="title-input-container">
                            <label for="">Title</label>
                            <input type="text" placeholder="Enter Note Title">
                        </div>
                        <div class="textarea-container">
                            <label for="">Points</label>
                            <textarea name="" id="" cols="20" rows="5"></textarea>
                        </div>
                    </div>
    
                    <div class="close-button-container">
                    <button
                        type="button"
                        class="close-button"
                        @click="closeModal"
                    >
                        Save
                    </button>
                    <button
                        type="button"
                        class="close-button"
                        @click="closeModal"
                    >
                        Cancel
                    </button>
                    </div>
                </DialogPanel>
                </TransitionChild>
            </div>
        </div>
      </Dialog>
    </TransitionRoot>
  </template>
  
  <script setup lang="ts">
    import { ref } from 'vue'
    import {
      TransitionRoot,
      TransitionChild,
      Dialog,
      DialogPanel,
      DialogTitle
    } from '@headlessui/vue'
  
    const isOpen = ref(false)
  
    function openModal() {
      isOpen.value = true
    }

    function closeModal() {
        isOpen.value = false
    }

  </script>

  <style scoped>
    .open-button {
        background-color: pink;
        color: white;
        padding: 20px;
    }

    .modal-dialog {
        position: relative;
    }

    .overly-transition {
        transition-duration: 2;
    }

    .modal-overlay {
        position: fixed;
        background-color: rgba(0, 0, 0, 0.5);
        bottom: 0;
        top: 0;
        left: 0;
        right: 0;
        z-index: 100;
        transition-duration: 2;
    }

    .modal-transition {
        
    }


    .modal-container {
        position: fixed;
        top: 0px;
        right: 0px;
        bottom: 0px;
        left: 0px;
        overflow-y: auto;
        z-index: 200;
    }

    .modal {
        display: flex;
        min-height: 100vh;
        align-items: center;
        justify-content: center;
        text-align: center;
    }

    .dialog-panel {
        width: 100vh;
        max-width: 28rem;
        overflow: hidden;
        border-radius: 10px;
        background-color: white;
        text-align: left;
        align-items: center;
        padding: 2%;
        transition: all 0.2s ease;
    }

    .modal-title {
        font-size: 18px;
        font-weight: medium;
        line-height: 24px;
        color: gray;
        /* text-lg font-medium leading-6 text-gray-900 */
    }

    .modal-info-container {
        display: flex;
        flex-direction: column;
        gap: 8px;
        margin-top: 0.5rem;
    }

    .title-input-container,
    .textarea-container {
        display: flex;
        flex-direction: column;
        gap: 8px;
        margin-top: 30px;
    }

    input,
    textarea {
        outline: none;
    }

    .close-button-container {
        display: flex;
        gap: 1rem;
        margin-top: 0.5rem;
        justify-content: right;
        margin-top: 1rem;
    }

    .close-button {
        min-width: 5rem;
        background-color: #71717a;
        color: white;
        border: none;
        border-radius: 5%;
        padding: 15px;
        cursor: pointer;
    }
  </style>