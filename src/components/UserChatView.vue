<template>
  <div class="user-card">
    <img :src="user.img" alt="User Image" class="user-img" />
    <h2>{{ user.nombre }}</h2>
    <div class="color-sample" :style="{ backgroundColor: color }"></div>
    <textarea v-model="newMessage" placeholder="Escribe un mensaje..."></textarea>
    <button @click="sendMessage">Enviar</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
  user: Object,
  color: String
});

const emit = defineEmits(['sendMessage']);
const newMessage = ref('');

// enviar mensaje
const sendMessage = () => {
  if (!newMessage.value.trim()) {
    alert('El mensaje no puede estar vacío.');
    return;
  }
  emit('sendMessage', newMessage.value);
  newMessage.value = '';
};
</script>

<style scoped>
.user-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: #000000;
  border: 1px solid #ddd;
  border-radius: 10px;
  padding: 1rem;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  width: 450px;
}

.user-img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
}

h2 {
  font-size: 1.2rem;
  margin: 0.5rem 0;
  color: greenyellow;
}

.color-sample {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  margin: 0.5rem 0;
}

textarea {
  width: 100%;
  height: 60px;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin: 0.5rem 0;
  resize: none;
}

button {
  padding: 0.5rem 1rem;
  background-color: #008CBA;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #005f73;
}
</style>
