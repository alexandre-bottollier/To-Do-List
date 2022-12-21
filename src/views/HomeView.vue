<script setup>
import TaskCreation from '@/components/TaskCreation.vue';
import TaskCard from '@/components/TaskCard.vue';
import { ref } from 'vue';

const tasks = ref([]);


function add(arg) {
  tasks.value.push(arg);
}

function remove(arg){
  tasks.value.splice(arg, 1);

}

const varTags = ref();


</script>

<template>
  <main>
      <TaskCreation @addTask="add" @sendTags="(arg) => {varTags = arg}"/>
      <TaskCard :id="index" :tags ="varTags" :title="titre" v-for = "(titre, index) in tasks" :key="index" @removeTask="remove"/>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  margin: auto;
  align-items: center;
}

</style>