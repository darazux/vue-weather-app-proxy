<!-- Results.vue -->

<template>
  <h2>気象データ</h2>
  <div>{{ results.country }}</div>
  <div>{{ results.cityName }}</div>
  <div>{{ results.temperature }}</div>
  <div v-if="results.icon">
    <img :src="results.icon" alt="icon" />
    <span>{{ results.conditionText }}</span>
  </div>
</template>

<script setup>
const props = defineProps({
  results: Object,
});
</script>
