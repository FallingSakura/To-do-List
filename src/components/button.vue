<script setup>
import { ref } from 'vue';

const props = defineProps(['text']);

const emit = defineEmits(['ok']);

function send() {
  emit('ok', 'Hi');
}
</script>

<template>
  <div @click="send" class="button">{{ props.text }}</div>
</template>

<style scoped>
.button {
  width: 100px;
  height: 50px;
  border-radius: 10px;
  line-height: 50px;
  background-color: aliceblue;
  text-align: center;
  margin: 100px;
  cursor: pointer;
  user-select: none;
}
</style>