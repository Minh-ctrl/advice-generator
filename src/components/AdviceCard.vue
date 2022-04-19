<script setup>
import { ref, reactive } from "vue";
const data = ref(null);
async function fetchData() {
  const req = await fetch("https://api.adviceslip.com/advice");
  const res = await req.json();
  data.value = res;
}
</script>
<template>
  <div class="container">
    <button @click="fetchData">clickme for data</button>
    <div v-if="data">
      {{ data }}
    </div>
  </div>
</template>
