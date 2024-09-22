<template>
  <div class="chat-header">
    <h1>{{ title }}</h1>
  </div>
</template>

<script setup>
const title = "chatAPI";
</script>

<style scoped>
.chat-header {
  background-color: #ffffff;
  color: #000000;
  text-align: center;
  font-family: 'Comic Sans MS', cursive, sans-serif;
}

h1 {
  font-size: 2rem;
}
</style>
