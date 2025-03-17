<template>
    <div>
      <h1>Simple Portfolio</h1>
      <p>Hello, this is my first portfolio website. My name is Jannatul Zaman and
        I am a current CS student at GSU. I have no idea why I chose CS.
      </p>
      <button @click="showWelcome = !showWelcome">
        {{ showWelcome ? 'Less' : 'More' }}
      </button>
      <p v-if="showWelcome">This website is a work in progress.</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const showWelcome = ref(true);
  </script>
  
  <style scoped>
  h1 {
    color: #2c3e50;
  }
  
  button {
    margin-top: 10px;
    padding: 10px 20px;
    cursor: pointer;
  }
  </style>