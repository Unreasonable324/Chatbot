<script setup lang="ts">
import ButtonCartFooter from "./ButtonCartFooter.vue";
import { computed, ref, watch } from "vue";
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

function sendMessage(message = '1231') {
  isMyMessage.value = !isMyMessage.value;
  messages.value.push({ message: message, isMyMessage: isMyMessage.value });
}
const maxH = computed(() => {
  sendMessage(window.screen.height+'')
  return window.screen.height - 50;
});
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
  <div class="main-wrapper" :style="`min-height: ${maxH+50}px; max-height: ${maxH+50}px`">
    <div class="messages" :style="`max-height: ${maxH}px`">
    <div class=" wrap" :style="`min-height: ${maxH}px`">
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
}
.messages {
  flex: 1;
  overflow: auto;
}
</style>
