<script setup>
import { ref } from "vue";

const name = ref("John Doe");
const race = ref("cat");
const tasks = ref(["talk", "eat the homework"]);
const link = "https://matiasm.com";

const toggleRace = () => {
  race.value = race.value === "cat" ? "dog" : "cat";
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="race === 'cat'">User is a cat! :3</p>
  <p v-else-if="race === 'dog'">User is a dog</p>
  <p v-else>Unknown race</p>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <a :href="link" target="_blank" rel="noopener">Link to my portfolio!</a>
  <br />
  <button @click="toggleRace">Change race</button>
</template>
<!-- <template>
  <h1 class="text-2xl">Vue Jobs</h1>
</template> -->

<style scoped></style>
