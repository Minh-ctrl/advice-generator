<script setup>
import {ref} from 'vue';
const props = defineProps(["data"]);
import IconDice from "../assets/IconDice.vue";
import PatternDividerDesktop from "../assets/PatternDividerDesktop.vue";

</script>
<template>
  <div class="containerCard flex flex-col flex-nowrap rounded-lg">
    <h3 class="id text-xs tracking-widest text-center self-center pt-5">
      ADVICE #{{ data.id }}
    </h3>
    <div class="advice self-center flex flex-row flex-nowrap justify-center">
      <h1 class="text-center text-2xl justify-self-center self-center pt-5">"{{ data.advice }}"
      </h1>
    </div>
    <div class="svgContainer flex flex-col flex-nowrap">
      <PatternDividerDesktop class="pattern block self-center mb-10" />
      <div class="containerofDice block">
        <div
          class="diceContainer flex flex-row justify-center flex-nowrap self-center bg-green-400 shadow-green-400 rounded-full"
        >
          <IconDice class="self-center" />
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
}
.pattern{
  top: 20%;
}
.diceContainer {
  width: 50px;
  height: 50px;
}
</style>
