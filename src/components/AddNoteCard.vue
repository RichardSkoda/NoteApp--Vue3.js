<template>
    <div class="plus-card">
        <font-awesome-icon icon="fa-solid fa-circle-plus" class="plus-icon" />
    </div>
</template>

<script setup lang="ts">
    import NotesModal from './NotesModal.vue';


</script>

<style scope>
    .plus-card {
        border: solid 2px #71717a;
        border-radius: 1%;
        color: white;
        cursor: pointer;
        opacity: 0.5;
        transition: all 0.2s ease;
        margin: 7%;
    }

    .plus-card:hover {
        opacity: 1;
        margin: 0;
        background-color: #71717a;
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