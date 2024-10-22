<script setup>
import { ref } from "vue";

const race = ref("cat");
const tasks = ref(["talk", "eat the homework"]);
const newTask = ref("");
const name = "John Doe";
const link = "https://matiasm.com";

const addTask = () => {
  if (!newTask.value.trim()) {
    return;
  }

  tasks.value.push(newTask.value);
  newTask.value = "";
};

const deleteTask = (index) => {
  tasks.value = tasks.value.filter((_, i) => i !== index);
};

const toggleRace = () => {
  race.value = race.value === "cat" ? "dog" : "cat";
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="race === 'cat'">User is a cat! :3</p>
  <p v-else-if="race === 'dog'">User is a dog</p>
  <p v-else>Unknown race</p>

  <form @submit.prevent="addTask">
    <label for="newTask">New Task</label>
    <br />
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <br />
    <button type="submit">Add Task</button>
  </form>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
        {{ " " }}
        <button @click="deleteTask(index)">X</button>
      </span>
    </li>
  </ul>
  <a :href="link" target="_blank" rel="noopener">Link to my portfolio!</a>
  <br />
  <button @click="toggleRace">Change race</button>
</template>
<!-- <template>
  <h1 class="text-2xl">Vue Jobs</h1>
</template> -->

<style scoped></style>
