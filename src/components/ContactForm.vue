<template>
    <div>
      <h2>Contact Us</h2>
      <form @submit.prevent="handleFormSubmit">
        <label for="name">Name:</label>
        <input v-model="contactForm.name" id="name" type="text" required />
        
        <label for="email">Email:</label>
        <input v-model="contactForm.email" id="email" type="email" required />
        
        <label for="message">Message:</label>
        <textarea v-model="contactForm.message" id="message" required></textarea>
        
        <button type="submit">Submit</button>
      </form>
    </div>
  </template>
  
  <script>
  import { ref, onMounted } from 'vue';
  
  export default {
    setup() {
      const contactForm = ref({
        name: '',
        email: '',
        message: ''
      });
  
      onMounted(() => {
        const savedFormData = localStorage.getItem('contactForm');
        if (savedFormData) {
          contactForm.value = JSON.parse(savedFormData);
        }
      });
  
      const handleFormSubmit = () => {
        localStorage.setItem('contactForm', JSON.stringify(contactForm.value));
        alert('Form submitted and data saved!');
      };
  
      return {
        contactForm,
        handleFormSubmit
      };
    }
  };
  </script>
  
  <style scoped>
  form {
    margin-top: 20px;
  }
  
  label {
    display: block;
    margin: 10px 0 5px;
  }
  
  input, textarea {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #000000;
  }
  
  button {
    padding: 10px;
    cursor: pointer;
    background-color: #000000;
    color: white;
    border: none;
  }
  
  button:hover {
    background-color: #696969;
  }
  </style>
  