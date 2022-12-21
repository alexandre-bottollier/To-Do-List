<script setup>

import { ref } from 'vue';
import TaskTags from '@/components/TaskTags.vue';

const emits = defineEmits(["addTask", "sendTags"]);
const trigger = ref(false);

function addTask () {
    emits('addTask', input.value.value);
    trigger.value = true;
    input.value.value = '';
}

const input = ref();

// function sendTags (tags) {
//     emits('sendTags', tags)
//     trigger.value = false;
// }

</script>

<template>

    <div class="container">
        <input @keypress.enter="addTask"
        type="text" 
        placeholder="Nouvelle tâche" 
        minlenght="1" 
        maxlength="20"
        ref="input"
        size="15"
        >

        <!-- <TaskTags @tags="sendTags"
        :trigger="trigger"/> -->

        <button type="button" @click="addTask" >✔️</button>
    </div>

</template>

<style scoped>
.container {
    margin-bottom: 20px;
    
}

input, button {
    padding: 10px;
    border-radius: 5px;
    margin: 5px;
}
</style>