<script setup>
import {ref} from 'vue';
const props = defineProps(["data"]);
import IconDice from "../assets/IconDice.vue";
import PatternDividerDesktop from "../assets/PatternDividerDesktop.vue";
const click = ref(null);
async function fetchData() {
  const req = await fetch("https://api.adviceslip.com/advice");
  const res = await req.json();
  click.value = res;
  console.log(click.value)
}
</script>
<template>
  <div
    class="containerCard bg-zinc-700 flex flex-col flex-nowrap rounded-md"
  >
    <h3 class="id text-xs tracking-widest text-center self-center pt-5">
      ADVICE #{{ data.id }}
    </h3>
    <div class="advice self-center flex flex-row flex-nowrap justify-center">
      <h1 class="text-center text-3xl justify-self-center self-center pt-5">"{{ data.advice }}"
      </h1>
    </div>
    <div class="svgContainer flex flex-col flex-nowrap">
      <PatternDividerDesktop class="mb-10 self-center" />
      <div
        class="diceContainer flex flex-row justify-center flex-nowrap self-center bg-green-400 shadow-green-400 rounded-full"
      >
        <IconDice @click="fetchData" class="self-center" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.id {
  color: hsl(150, 100%, 66%);
}
.containerCard {
  height: 300px;
  width: 550px;
  color: hsl(218, 23%, 16%);
}
.advice {
  color: #cee3e8;
  height: 400px;
  width: 500px;
}
.svgContainer {
}
.diceContainer {
  width: 50px;
  height: 50px;
}
</style>
