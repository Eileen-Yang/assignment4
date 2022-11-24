<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import Movies from './components/movies.vue'
</script>

<template>
  <div class="app-container">
    <Suspense>
      <Movies/>
    </Suspense>
  </div>
</template>

<style scoped>
  .app-container {
    background-image: url(https://visme.co/blog/wp-content/uploads/2017/07/50-Beautiful-and-Minimalist-Presentation-Backgrounds-036.jpg);
  }
</style>
