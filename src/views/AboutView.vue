<script setup>
import AdviceCard from "../components/AdviceCard.vue";
</script>
<template>
  <div class="about">
    <AdviceCard />
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
