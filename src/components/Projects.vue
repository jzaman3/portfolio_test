<template>
  <div>
    <h2>My Projects</h2>
    <p v-if="projects.length === 0">No projects available.</p>
    <ul>
      <li v-for="(project, index) in projects" :key="index">
        <h3>{{ project.name }}</h3>
        <p>{{ project.description }}</p>
      </li>
    </ul>
    <h3>Number of Projects: {{ projectSummary }}</h3>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const projects = ref([
  {
    name: "PlanPal",
    description: "A website where users can login and manage tasks for organization. Made with React.",
  }
]);

const projectSummary = computed(() => `${projects.value.length} projects`);
</script>

<style scoped>
ul {
  list-style: none;
}

li {
  margin-bottom: 20px;
}

h3 {
  color: #34495e;
}
</style>
