<script setup>
import BlogPost from "./components/BlogPost.vue";
import { ref } from "vue";

const postList = ref([
  { id: 1, title: "Mucho calor en Enseyork", content: "Contenido1" },
  { id: 2, title: "titulo dosss" },
  { id: 3, title: "titulo tres", content: "contenido de tarjeta tres" },
  { id: 4 },
]);
console.log(postList);
</script>
<template>
  <div class="card">
    <!-- <BlogPost :id="1" title="Mucho calor en ensenada" />
    <BlogPost :id="2" title="Mucho calor en ensenada" content="Esto es un contenido tambien" />
    <BlogPost :id="3" content="Esto es un contenido tambien" />
    <BlogPost :id="4" textColor="text-orange-500" />
    <BlogPost :id="5" colorFondo="#000" /> -->
    <BlogPost
      v-for="post in postList"
      :id="`${post.id}`"
      :title="`${post.title}`"
      :content="`${post.content}`"
    />
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
