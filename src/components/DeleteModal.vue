<template>
    <TransitionRoot appear :show="isOpen" as="template">
      <Dialog as="div" @close="closeModal" class="relative z-10">
        <TransitionChild
          as="template"
          enter="duration-300 ease-out"
          enter-from="opacity-0"
          enter-to="opacity-100"
          leave="duration-200 ease-in"
          leave-from="opacity-100"
          leave-to="opacity-0"
        >
          <div class="fixed inset-0 bg-black bg-opacity-25" />
        </TransitionChild>
  
        <div class="fixed inset-0 overflow-y-auto">
          <div
            class="flex min-h-full items-center justify-center p-4 text-center"
          >
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
                class="w-full max-w-md transform overflow-hidden rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all"
              >
                <DialogTitle
                  as="h3"
                  class="text-lg font-medium leading-6 text-gray-900"
                >
                  Delete
                </DialogTitle>
                <div class="mt-2">
                  <p class="text-sm text-gray-500">
                    Are you sure you want to delete this note?
                  </p>
                </div>
  
                <div class="buttons-container">
                        <button
                            type="button"
                            class="button"
                            @click="closeModal"
                        >
                            Ok
                        </button>
                        <button
                            type="button"
                            class="button"
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
  import { ref, watch } from 'vue'
  import {
    TransitionRoot,
    TransitionChild,
    Dialog,
    DialogPanel,
    DialogTitle,
  } from '@headlessui/vue'
  
    const isOpen = ref(false)

    // set props
    interface Props {
        openModal: boolean
    }

    const props = withDefaults(defineProps<Props>(), {
        openModal: false
    })

    // set emit
    const emit = defineEmits<{
    (e: 'showdeletemodal', id: boolean): void
    }>()

    watch(props,() => {
        isOpen.value = props.openModal
    })
  
  function closeModal() {
    emit('showdeletemodal', false)
    isOpen.value = false
  }

  </script>

  <style scoped>
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
        border: solid 1px #71717a;
        border-radius: 5px;
        padding: 10px 15px;
        cursor: pointer;
        transition: all 0.2s ease;
    }

    button:hover {
      background-color: #71717a;
      color: white;
    }
  </style>
  