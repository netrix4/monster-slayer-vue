<script setup>
defineProps(["title", "content"]);
</script>
<template>
  <div class="card-body">
    <h2 v-if="title" class="card-title">{{ title }}</h2>
    <h2 v-else class="card-title">Esto es un titulo por defecto</h2>
    <p v-if="content">
      {{ content }}
    </p>
    <p v-else>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nisi, esse? Tenetur fuga minus
      laborum cumque obcaecati! Magni nulla tenetur illum illo minima sed velit voluptatem suscipit
      facilis, dolore doloremque veniam?
    </p>
  </div>
</template>
<style>
@import "tailwindcss";

.card-body {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 1%;
  background: linear-gradient(270deg, #59848f, #00ccff);
  border: 10px;
  border-radius: 1%;
  padding: 2%;
  box-shadow: #00000025 10px 10px 20px;
}
.card-title {
  font-weight: bold;
  font-size: larger;
}
</style>
