<template>
  <div id="app">
    <Navbar />       <!-- Navbar global -->
    <router-view />  <!-- Halaman spesifik muncul di sini -->
  </div>
</template>

<script setup>
import Navbar from './components/Navbar.vue'
</script>

<style>
body {
  margin: 0;
  font-family: 'Poppins', sans-serif;
  background-image: url('@/assets/Bg.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
}
</style>
