<template>
  <div class="chat-app">
    <ChatHeaderView />

    <div class="chat-main">
      <!-- user 1 -->
      <UserChatView
        :user="user1"
        color="lightblue"
        @sendMessage="handleSendMessageUser1"
        class="user-left"
      />

      <!-- caja del chat -->
      <div class="chat-container">
        <MessageListView :messages="messages" />
      </div>

      <!-- user 2  -->
      <UserChatView
        :user="user2"
        color="beige"
        @sendMessage="handleSendMessageUser2"
        class="user-right"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";

import ChatHeaderView from "./components/ChatHeaderView.vue";
import MessageListView from "./components/MessageListView.vue";
import UserChatView from "./components/UserChatView.vue";


const user1 = ref({});
const user2 = ref({});
const messages = ref([]);

// user 1 
const handleSendMessageUser1 = (message) => {
  messages.value.push({
    sender: user1.value.nombre,
    text: message,
    color: "lightblue",
    alineacion: "izquierda",
    img: user1.value.img,
  });
};

// user 2
const handleSendMessageUser2 = (message) => {
  messages.value.push({
    sender: user2.value.nombre,
    text: message,
    color: "beige", 
    alineacion: "derecha",
    img: user2.value.img,
  });
};

// obtener usuarios random
onMounted(async () => {
  try {
    const response1 = await axios.get("https://randomuser.me/api/");
    const response2 = await axios.get("https://randomuser.me/api/");

    user1.value = {
      nombre: `${response1.data.results[0].name.first} ${response1.data.results[0].name.last}`,
      img: response1.data.results[0].picture.large,
    };

    user2.value = {
      nombre: `${response2.data.results[0].name.first} ${response2.data.results[0].name.last}`,
      img: response2.data.results[0].picture.large,
    };
  } catch (error) {
    console.log("Error fetching users:", error);
  }
});
</script>

<style scoped>
.chat-app {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.chat-main {
  display: flex;
  justify-content: space-between;
  width: 100%;
  max-width: 1200px;
}

.chat-container {
  width: 80%;
  max-height: 400px;
  overflow-y: auto;
  border: 2px solid #ccc;
  padding: 10px;
  border-radius: 10px;
  background-image: url('./assets/back.jpg'); 
  background-size: cover; 
  background-position: center;
}

.user-left {
  flex: 1;
  display: flex;
  justify-content: flex-start;
}

.user-right {
  flex: 1;
  display: flex;
  justify-content: flex-end;
}
</style>
