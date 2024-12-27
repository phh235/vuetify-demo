<template>
  <v-app class="container">
    <v-main class="d-flex justify-center align-center">
      <v-btn variant="tonal" color="deep-purple-darken-1" @click="loginWithGoogle">
        <v-icon class="mr-2">mdi-google</v-icon>
        <span style="user-select: none !important;">Sign in with Google</span>
      </v-btn>
    </v-main>
  </v-app>
</template>

<script setup>
const loginWithGoogle = async () => {
  const clientId = import.meta.env.VITE_GOOGLE_CLIENT_ID;
  const redirectUri = import.meta.env.VITE_GOOGLE_REDIRECT_URI;
  const scope = 'https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/userinfo.email';
  const responseType = 'token';
  const authUrl = `https://accounts.google.com/o/oauth2/v2/auth?client_id=${clientId}&redirect_uri=${redirectUri}&scope=${scope}&response_type=${responseType}`;
  window.location.href = authUrl;
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
</style>