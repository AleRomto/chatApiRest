<template>
  <div class="message-list">
    <div
      v-for="(message, index) in messages"
      :key="index"
      class="message"
      :class="message.alineacion"
      :style="{ backgroundColor: message.color }"
    >
      <p class="message-text">{{ message.text }}</p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  messages: Array
});
</script>

<style scoped>
.message-list {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 10px;
  overflow-y: auto;
  padding: 1rem;
}

.message {
  padding: 10px;
  border-radius: 10px;
  max-width: 60%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  word-break: break-word;
}

.message.derecha {
  align-self: flex-end;
  color: #000000;
}

.message.izquierda {
  align-self: flex-start;
  color: #000000;
}

.message-header {
  display: flex;
  align-items: center;
  gap: 10px;
}

.message-text {
  margin-top: 5px;
}
</style>
