<script setup lang="ts">
import ButtonCartFooter from "./ButtonCartFooter.vue";
import {  ref, watch } from "vue";
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
  { message: "last3", isMyMessage: false },
]);
let count = 0 

function sendMessage() {
  count++
  isMyMessage.value = !isMyMessage.value;
  messages.value.push({ message: count+'', isMyMessage: isMyMessage.value });
}
// const maxH = computed(() => {
//   sendMessage(window.screen.height+'')
//   return window.screen.height - 50;
// });
const itemRefs = ref([]);
function lastMessageScroll(b: string) {
  var e = itemRefs.value;

  if (!e) return;
  setTimeout(() => {
    //@ts-ignore
    e.scrollIntoView({
      behavior: b || "auto",
      block: "end",
    });
  }, 0);
}
watch(messages.value, () => {
  lastMessageScroll("smooth");
  
});

</script>
<template>
  <div class="main-wrapper" >
    <div class="messages" >
    <div class=" wrap" >
      <div class="message" v-for="i in messages">{{ i.message }}</div>
    </div>
    <div class="" ref="itemRefs"></div>
    </div>

    <ButtonCartFooter v-model="message" @sendMessage="sendMessage"></ButtonCartFooter>
  </div>
</template>
<style>
.main-wrapper {
  display: flex;
  flex-direction: column;
}
.wrap{
  display: flex;
  flex-direction: column;
  gap: 4px;
  justify-content: flex-end;
  min-height: calc(100vh - 50px);

}
.messages {
  flex: 1;
  overflow: auto;
  max-height: calc(100vh - 50px);
}
</style>
