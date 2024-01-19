<!-- From.vue -->

<template>
  <form>
    <input type="text" v-model="city" placeholder="都市名を英語で入力" />
    {{ city }}
    <button type="submit">Get Weather</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const city = ref('');
</script>
