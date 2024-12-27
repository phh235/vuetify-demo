<template>
  <v-app class="container">
    <v-main class="d-flex justify-center align-center">
      <div>Loading...</div>
    </v-main>
  </v-app>
</template>

<script setup>
import { onMounted } from 'vue';

onMounted(() => {
  const hash = window.location.hash.substring(1);
  const params = new URLSearchParams(hash);
  const accessToken = params.get('access_token');

  if (accessToken) {
    fetch('https://www.googleapis.com/oauth2/v1/userinfo?alt=json&access_token=' + accessToken)
      .then(response => response.json())
      .then(user => {
        localStorage.setItem('user', JSON.stringify(user));
        window.location.href = '/home';
      })
      .catch(error => {
        console.error('Error fetching user info:', error);
      });
  }
});
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
</style>