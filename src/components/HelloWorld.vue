<script setup>
import { ref } from 'vue';

let id = 0;
const task = ref('');

const toDos = ref([]);

const newTask = () => {
  toDos.value.push({
    id: id++,
    text: task.value,
  });
  task.value = '';
};

const deleteTask = (t) => {
  toDos.value = toDos.value.filter((i) => i !== t);
};
</script>

<template>
  <input v-model="task" type="text" />
  <li v-for="toDo in toDos" :key="toDo.id">
    {{ toDo.text }}
    <button @click="deleteTask(toDo)">Deletar</button>
  </li>
  <button @click="newTask">Adicionar tarefa</button>
</template>

<style scoped></style>
