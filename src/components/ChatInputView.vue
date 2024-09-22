<template>
  <form @submit.prevent="sendMessage">
    <textarea v-model="newMessage" placeholder="Escribe un mensaje..."></textarea>
    <button type="submit">Enviar</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const emit = defineEmits(['sendMessage']);
const newMessage = ref("");

const sendMessage = () => {
  if (!newMessage.value.trim()) {
    alert("El mensaje no puede estar vacío.");
    return;
  }
  emit('sendMessage', {
    text: newMessage.value,
    color: getRandomColor(),
    alineacion: Math.random() > 0.5 ? 'izquierda' : 'derecha'
  });
  newMessage.value = "";
};

const getRandomColor = () => {
  const colors = ['#ff6347', '#4682b4', '#32cd32', '#ff1493'];
  return colors[Math.floor(Math.random() * colors.length)];
};
</script>

<style scoped>
form {
  display: flex;
  gap: 10px;
  align-items: center;
}
textarea {
  flex: 1;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-family: 'Press Start 2P', sans-serif;
}
button {
  padding: 10px;
  background-color: #00d2ff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-family: 'Press Start 2P', sans-serif;
}
button:hover {
  background-color: #00aaff;
}
</style>
