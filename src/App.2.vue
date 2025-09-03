<script setup>
import BlogPost from "./components/BlogPost.vue";
</script>
<template>
  <div class="card">
    <BlogPost title="Mucho calor en ensenada" />
    <BlogPost title="Mucho calor en ensenada" content="Esto es un contenido tambien" />
    <BlogPost content="Esto es un contenido tambien" />
  </div>
</template>
<style lang="css">
/* @import "tailwindcss"; */
.card {
  display: flex;
  flex-direction: column;
  padding-top: 5%;
  padding-bottom: 5%;
  padding-left: 15%;
  padding-right: 15%;
  gap: 1%;
  background-color: #00ab67;
  height: 100vh;
  width: 100%;
}
</style>
