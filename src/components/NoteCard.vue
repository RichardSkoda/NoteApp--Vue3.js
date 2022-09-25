<template>
    <div class="note-card-container">
        <div class="title-container">
            <h1>Title</h1>
            <p>Points</p>
        </div>
        <div class="icon-container">
            <font-awesome-icon icon="fa-solid fa-pen-nib" class="icon" />
            <font-awesome-icon icon="fa-solid fa-trash-can" class="icon" @click="deleteNoteModal" />
        </div>
    </div>
</template>

<script setup lang="ts">

    // set emit
    const emit = defineEmits<{
        (e: 'showdeletemodal', id: boolean): void
    }>()

    const deleteNoteModal = () => {
        emit('showdeletemodal', true)
    }

</script>

<style scoped>
    .note-card-container {
        display: flex;
        justify-content: space-between;
        min-height: 300px;
        max-height: 50vh;
        background-color: #71717a;
        border-radius: 1%;
    }

    .title-container {
        display: flex;
        flex-direction: column;
        color: white;
        margin: 10px;
    }

    .icon-container {
        display: flex;
        gap: 10px;
        margin: 10px;
        justify-content: right;
    }

    .icon {
        color: white;
        font-size: 20px;
        cursor: pointer;
        transition: all 0.2s ease;
    }

    .icon:hover {
        opacity: 0.5;
    }

</style>