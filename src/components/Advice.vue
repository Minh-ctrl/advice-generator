<script setup>
import { ref } from "vue";
import Card from "./Card.vue";
const data = ref(null);
async function fetchData() {
  const req = await fetch("https://api.adviceslip.com/advice");
  const res = await req.json();
  data.value = res;
}
</script>
<template>
  <div class="containerupper">
    <button @click="fetchData">clickme for data</button>
    <div v-if="data">
      <Card :data="data.slip" />
    </div>
  </div>
</template>
