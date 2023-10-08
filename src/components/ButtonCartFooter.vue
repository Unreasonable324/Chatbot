<template>
  <div class="ButtonCartFooter-wrapper">
    <input type="text" :value="modelValue" @input="handler" /> <button @click="sendMessage">send</button>
  </div>
</template>

<script setup lang="ts">
import { PropType } from "vue";

defineProps({
  modelValue: {
    type: String as PropType<string | null | number>,
    default: "",
  },
});
const emit = defineEmits(["update:modelValue",'sendMessage']);
function sendMessage() {
  emit('sendMessage')
}
function handler(event: any) {
  emit("update:modelValue", event.target.value);
}
</script>

<style>
.ButtonCartFooter-wrapper {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  border-radius: 4px 4px 0 0;
  height: 50px;
  padding: 15px 5px;
  background: var(--tg-theme-button-color);
  display: flex;
  gap: 5px;
  /* background: red; */
}
.ButtonCartFooter-wrapper input{
  width: 100%;
  height: 100%;
  padding: 5px;
  border-radius: 5px;
}
.ButtonCartFooter-wrapper button {
  width: 100px;
  padding: 5px;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
