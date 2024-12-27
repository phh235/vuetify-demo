<template>
  <v-app class="container">
    <v-main class="d-flex justify-center align-center flex-column">
      <div v-if="user" class="text-center">
        <h1 class="display-1 mb-4">Welcome, {{ user.name }} <span><img
              src="https://em-content.zobj.net/source/apple/391/hear-no-evil-monkey_1f649.png" alt="kon khi kho"
              width="60"></span></h1>
        <v-btn variant="tonal" color="deep-purple-darken-1" @click="logout">
          <v-icon class="mr-2">mdi-logout</v-icon>
          <span style="user-select: none !important;">Logout</span>
        </v-btn>
      </div>
      <div v-else class="text-center">
        <h1 class="display-1">Welcome, Guest!</h1>
      </div>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const user = ref(null);

onMounted(() => {
  const userData = localStorage.getItem('user');
  if (userData) {
    user.value = JSON.parse(userData);
  }
});

const logout = () => {
  localStorage.removeItem('user');
  window.location.href = '/login';
}
</script>

<style scoped>
.container {
  width: 100%;
  height: 100%;
  background-color: #ede7f6;
  background-image: radial-gradient(rgba(000, 000, 000, 0.171) 2px, transparent 0);
  background-size: 30px 30px;
  background-position: -5px -5px;
}

.flex-column {
  flex-direction: column;
}

.display-1 {
  font-size: 3rem;
  line-height: 1.5;
  font-weight: 300;
  letter-spacing: 0.0071428571em;
  margin-bottom: 1rem;
}

@media (min-width: 420px) {
  .display-1 {
    font-size: 3.5rem;
  }
}

@media (min-width: 600px) {
  .display-1 {
    font-size: 4rem;
  }
}

@media (min-width: 960px) {
  .display-1 {
    font-size: 4.5rem;
  }
}

@media (min-width: 1264px) {
  .display-1 {
    font-size: 5rem;
  }
}
</style>
