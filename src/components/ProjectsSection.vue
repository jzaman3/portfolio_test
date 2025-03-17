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
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const projects = ref([
    
  ]);
  </script>
  
  <style scoped>
  ul {
    list-style: none;
    padding: 0;
  }
  
  li {
    margin-bottom: 20px;
  }
  
  h3 {
    color: #34495e;
  }
  </style>