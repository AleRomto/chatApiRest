<template>
  <div class="message" :style="{ alignSelf: message.alineacion === 'izquierda' ? 'flex-start' : 'flex-end' }">
    <img :src="message.img" alt="User Image" class="message-img" />
    <div class="message-text" :style="{ backgroundColor: message.color }">
      <p><strong>{{ message.sender }}:</strong> {{ message.text }}</p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  message: Object
});
</script>

<style scoped>
.message {
  padding: 1rem;
  border-radius: 15px;
  color: #fff;
  max-width: 60%;
}
</style>
