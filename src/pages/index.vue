<template>
  <v-app class="container">
    <v-main class="d-flex justify-center align-center flex-column">
      <div v-if="user">
        <h1>Welcome, {{ user.name }} <span><img
              src="https://em-content.zobj.net/source/apple/391/hear-no-evil-monkey_1f649.png" alt="kon khi kho"
              width="35"></span></h1>
        <v-btn variant="tonal" color="deep-purple-darken-1" @click="logout" class="mt-4">
          <v-icon class="mr-2">mdi-logout</v-icon>
          <span style="user-select: none !important;">Logout</span>
        </v-btn>
      </div>
      <div v-else>
        <h1>Welcome, Guest!</h1>
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

.mt-4 {
  margin-top: 1rem;
}
</style>