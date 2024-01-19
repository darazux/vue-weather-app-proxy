<!-- App.vue -->

<template>
  <div class="wrapper">
    <div class="container">
      <Title />
      <Form @submit-form="getWeather" />
      <Results :results="results" v-if="!loading" />
      <Loading v-if="loading" />
    </div>
  </div>
</template>

<script setup>
import axios from 'axios';
import Title from './components/Title.vue';
import Form from './components/Form.vue';
import Results from './components/Results.vue';
import Loading from './components/Loading.vue';
import { reactive, ref } from 'vue';
import './assets/base.css';

const loading = ref(false);

const results = reactive({
  country: '',
  cityName: '',
  temperature: '',
  conditionText: '',
  icon: '',
});

const getWeather = (city) => {
  loading.value = true;
  axios
    .get(`https://proxy-server-node.vercel.app/weather-data?${city}`)
    .then((res) => {
      (results.country = res.data.location.country),
        (results.cityName = res.data.location.name),
        (results.temperature = res.data.current.temp_c),
        (results.conditionText = res.data.current.condition.text),
        (results.icon = res.data.current.condition.icon);
      loading.value = false;
    })
    .catch((err) =>
      alert('エラーが発生しました。ページをリロードしてください。'),
    );
};
</script>
