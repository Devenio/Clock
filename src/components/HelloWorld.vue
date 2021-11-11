<template>
  <div class="bg-black w-screen h-screen flex items-center justify-center">
    <div class="text-center font-light timer">
      {{ hours < 10 ? `0${hours}` : hours }}:{{ minutes < 10 ? `0${minutes}` : minutes }}:{{ seconds < 10 ? `0${seconds}` : seconds }}
      <span class="text-3xl" style="margin-left: -40px">{{ hours <= 12 ? 'AM' :'PM'}}</span>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const hours = ref(23);
const minutes = ref(59);
const seconds = ref(50);

setInterval(() => {
  seconds.value++;
  if (seconds.value >= 60) {
    seconds.value = 0;
    minutes.value++;
  }
  if (minutes.value >= 60) {
    minutes.value = 0;
    hours.value++;
  }
  if (hours.value >= 24) {
    hours.value = 0;
  }
}, 1000);
</script>

<style scoped>
.timer {
  font-size: 15rem;
  color: #08bd00;
}
</style>
