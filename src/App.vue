<!-- App.vue -->

<template>
  <Title />
  <Form @submit-form="getWeather" />
</template>

<script setup>
import axios from 'axios';
import Title from './components/Title.vue';
import Form from './components/Form.vue';

const getWeather = (city) => {
  axios
    .get(`https://proxy-server-node.vercel.app/weather-data?${city}`)
    .then((res) => console.log(res));
};
</script>
