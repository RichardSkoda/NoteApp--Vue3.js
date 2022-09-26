<template>
    <TransitionRoot appear :show="isOpen" as="template">
      <Dialog as="div" @close="closeModal" class="modal-dialog">
        <TransitionChild
          as="template"
          enter="duration-300 ease-out"
          enter-from="opacity-0"
          enter-to="opacity-100"
          leave="duration-200 ease-in"
          leave-from="opacity-100"
          leave-to="opacity-0"
        >
            <div class="modal-overlay"></div>
        </TransitionChild>

        <div class="modal-container">
            <div class="modal">
                <TransitionChild
                    as="template"
                    enter="duration-300 ease-out"
                    enter-from="opacity-0 scale-95"
                    enter-to="opacity-100 scale-100"
                    leave="duration-200 ease-in"
                    leave-from="opacity-100 scale-100"
                    leave-to="opacity-0 scale-95"
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
                            <input type="text" v-model="title" placeholder="Enter Note Title">
                        </div>
                        <div class="textarea-container">
                            <label for="">Points</label>
                            <textarea v-model="point" name="" id="" cols="20" rows="5"></textarea>
                        </div>
                    </div>
    
                    <div class="buttons-container">
                        <button
                            type="button"
                            class="button"
                            @click="closeModal"
                        >
                            Cancel
                        </button>
                        <button
                            type="button"
                            class="button"
                            @click="saveNote"
                        >
                            Save
                        </button>
                    </div>
                </DialogPanel>
                </TransitionChild>
            </div>
        </div>
      </Dialog>
    </TransitionRoot>
    <div></div>
  </template>
  
  <script setup lang="ts">
    import { ref, watch } from 'vue'
    import {
      TransitionRoot,
      TransitionChild,
      Dialog,
      DialogPanel,
      DialogTitle
    } from '@headlessui/vue'

    import { newNote } from '../common.interface';
  
    const isOpen = ref(false)
    const title = ref('')
    const point = ref('')

    // set props
    interface Props {
        openModal: boolean
    }

    const props = withDefaults(defineProps<Props>(), {
        openModal: false
    })

    // set emit
    const emit = defineEmits<{
        (e: 'showmodal', id: boolean): void
        (e: 'savenote', value: newNote): void
    }>()

    watch(props,() => {
        isOpen.value = props.openModal
    })

    // function send false to showModal in App.vue after modal close. It is done by emit()
    function closeModal() {
        emit('showmodal', false)
        isOpen.value = false
    }

    const saveNote = () => {
        emit('showmodal', false)
        let newNote = {
            title:title.value,
            point:point.value
        }
        emit('savenote', newNote)
    }
  </script>

  <style scoped>
    .modal-dialog {
        position: relative;
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
        border: solid 1px #71717a;
        border-radius: 5px;
    }

    .buttons-container {
        display: flex;
        gap: 1rem;
        margin-top: 0.5rem;
        justify-content: right;
        margin-top: 1rem;
    }

    .button {
        min-width: 5rem;
        color: #71717a;
        /* border: solid 1px #71717a; */
        border-radius: 5px;
        padding: 10px 15px;
        cursor: pointer;
        transition: all 0.2s ease;
    }

    button:hover {
      background-color: rgb(209, 128, 142);
      color: white;
    }
  </style>