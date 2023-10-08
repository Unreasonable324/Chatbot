<script setup lang="ts">
import ButtonCartFooter from "./ButtonCartFooter.vue";
import { ref } from "vue";
const message = ref("123");
const isMyMessage = ref(false);
const messages = ref([
  { message: "text", isMyMessage: true },
  { message: "text", isMyMessage: false },
  { message: "text", isMyMessage: true },
  { message: "text", isMyMessage: false },
  { message: "text", isMyMessage: true },
  { message: "text", isMyMessage: false },
  { message: "text", isMyMessage: true },
  { message: "text", isMyMessage: false },
  { message: "text", isMyMessage: true },
  { message: "text", isMyMessage: false },
  { message: "text", isMyMessage: true },
  { message: "text", isMyMessage: false },
  { message: "text", isMyMessage: true },
  { message: "text", isMyMessage: false },
  { message: "text", isMyMessage: true },
  { message: "last", isMyMessage: false },
]);

function sendMessage() {
  isMyMessage.value = !isMyMessage.value;
  messages.value.push({ message: message.value, isMyMessage: isMyMessage.value });
}
</script>
<template>
  <div class="main-wrapper">
    <div class="page">
      <div class="chat_wrapper">
        <div
          class="chat_message"
          v-for="i in messages"
          :style="i.isMyMessage ? 'align-items: flex-start;' : 'align-items: flex-end;'"
        >
        <span>
          {{ i.message }}
        
        </span>
        </div>
      </div>

      <ButtonCartFooter v-model="message" @sendMessage="sendMessage"></ButtonCartFooter>
    </div>
  </div>
</template>
<style>
.page {
  width: 100%;
  /* position: absolute; */
  /* top: 30px; */
}
.page {
}
.chat_wrapper {
  display: grid;
  /* display: flex;
  flex-direction: column; */
  gap: 5px;
}
.chat_message {
  display: flex;
  flex-direction: column;
}
.chat_message span{
width: min-content;
background: var(--tg-theme-link-color);
padding: 5px;
border-radius: 5px;

}
</style>
