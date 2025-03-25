<template>
  <div>
    <nav class="sidebar">
      <ul>
        <li><button @click="scrollToSection('home')">Home</button></li>
        <li><button @click="scrollToSection('projects')">Projects</button></li>
        <li><button @click="scrollToSection('contact')">Contact</button></li>
      </ul>
    </nav>

    <div class="content">
      <section id="home" ref="home" class="fade">
        <Home />
      </section>

      <section id="projects" ref="projects" class="fade">
        <Projects />
      </section>

      <section id="contact" ref="contact" class="fade">
        <ContactForm />
      </section>

      <div>
        <h2>Visitor Counter</h2>
        <p>Number of visitors (page loads): {{ visitorCount }}</p>

        <h2>Click Counter</h2>
        <button @click="incrementCounter">Click Me!</button>
        <p>You have clicked the button {{ counter }} times.</p>
      </div>

      <div>
        <button @click="toggleMessage">{{ showMessage ? 'Hide' : 'Show' }} Message</button>
        <p v-show="showMessage">Hello, you have found the hidden cat!</p>
        <img v-show="showMessage" src="/src/assets/avatar.jpg" alt="Cat" />
      </div>
    </div>
  </div>
</template>

<script>
import { ref, computed, onMounted } from 'vue';
import Home from './components/Home.vue';
import Projects from './components/Projects.vue';
import ContactForm from './components/ContactForm.vue';

export default {
  components: {
    Home,
    Projects,
    ContactForm
  },
  setup() {
    const home = ref(null);
    const projects = ref(null);
    const contact = ref(null);

    const visitorCount = ref(0);
    onMounted(() => {
      const savedVisitorCount = localStorage.getItem('visitorCount');
      if (savedVisitorCount) {
        visitorCount.value = parseInt(savedVisitorCount);
      }
      visitorCount.value++;
      localStorage.setItem('visitorCount', visitorCount.value);
    });

    const counter = ref(0);
    const incrementCounter = () => {
      counter.value++;
    };

    const showMessage = ref(false);
    const toggleMessage = () => {
      showMessage.value = !showMessage.value;
    };

    const projectsList = ref([]);
    const projectSummary = computed(() => {
      return `${projectsList.value.length} projects`;
    });

    const scrollToSection = (section) => {
      if (section === 'home') home.value.scrollIntoView({ behavior: 'smooth' });
      if (section === 'projects') projects.value.scrollIntoView({ behavior: 'smooth' });
      if (section === 'contact') contact.value.scrollIntoView({ behavior: 'smooth' });
    };

    return {
      home,
      projects,
      contact,
      scrollToSection,
      counter,
      incrementCounter,
      showMessage,
      toggleMessage,
      visitorCount,
      projectsList,
      projectSummary
    };
  }
};
</script>

<style scoped>
nav button {
  margin: 5px;
  padding: 10px;
}

button {
  padding: 10px;
  cursor: pointer;
  margin-left: 250px;
}

p {
  margin-top: 10px;
  margin-left: 250px;
}

h2 {
  margin-top: 20px;
  margin-left: 250px;
}

p {
  font-size: 1.2rem;
}

ul {
  list-style-type: none;
}

input,
textarea {
  margin: 10px 0;
  padding: 5px;
}

.fade {
  animation: fadeIn 1s ease-in-out;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
