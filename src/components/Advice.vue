<script setup>
import { ref } from "vue";
import IconDice from "../assets/IconDice.vue";
import PatternDividerDesktop from "../assets/PatternDividerDesktop.vue";
const data = ref(null);
async function fetchData() {
  const req = await fetch("https://api.adviceslip.com/advice");
  const res = await req.json();
  data.value = res.slip;
}
</script>
<template>
  <div class="containerupper">
    <div class="containerCard flex flex-col flex-nowrap rounded-lg">
      <h3
        v-if="data"
        class="id text-xs tracking-widest text-center self-center pt-5"
      >
        ADVICE #{{ data.id }}
      </h3>
      <h3
        v-else
        class="id text-xs tracking-widest text-center self-center pt-5"
      >
        ADVICE #NUM
      </h3>
      <div class="advice self-center flex flex-row flex-nowrap justify-center">
        <h1
          v-if="data"
          class="text-center text-2xl justify-self-center self-center pt-5"
        >
          "{{ data.advice }}"
        </h1>
        <h1
          v-else
          class="text-center text-2xl justify-self-center self-center pt-5"
        >
          Click the Dice for random advice!
        </h1>
      </div>
      <div class="svgContainer flex flex-col flex-nowrap">
        <PatternDividerDesktop class="pattern block self-center mb-10" />
        <div class="containerofDice block">
          <div
            class="diceContainer cursor-pointer flex flex-row justify-center flex-nowrap self-center bg-green-400 shadow-green-400 rounded-full"
          >
            <IconDice @click="fetchData" class="IconDice self-center" />
          </div>
        </div>
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
  background-color: hsl(218, 23%, 16%);
}
.advice {
  color: #cee3e8;
  height: 450px;
  width: 500px;
}
.containerofDice {
  left: 45%;
  top: 25%;
  width: 50px;
}
.pattern {
  top: 20%;
}
.diceContainer {
  width: 50px;
  height: 50px;
}
.diceContainer:hover {
  color: hsl(150, 100%, 66%);
  box-shadow: 0 0px 20px hsl(150, 100%, 66%);
  opacity: 1;
  transition: 0.5s;
}
.IconDice:hover {
  animation: slide 5s infinite;
}
@keyframes slide {
  0% {
    transform: rotate(0deg);
  }
  25% {
    transform: rotate(359deg);
  }
  50% {
    transform: rotate(0deg);
  }
  72.5% {
    transform: rotate(359deg);
  }
}
</style>
