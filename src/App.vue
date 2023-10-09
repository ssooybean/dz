<script setup>
import Header from '@/components/Header.vue';
import Search from '@/components/Search.vue';
import Chart from '@/components/Chart.vue';
import axios from 'axios';
</script>

<template>
  <Header />
  <Search @search="search" />
  <Chart v-if="chartValue.length" v-bind:req="chartValue" />
</template>

<script>
export default {
  data() {
    return {
      chartValue: {},
    };
  },
  methods: {
    search(req) {
      axios
        .get(
          `https://api.weatherbit.io/v2.0/history/daily?city=${req.city}&start_date=${req.from}&end_date=${req.to}&key=3549b3f6bfdb4cf6a5fa7318b057dfd0`,
        )
        .then((res) => {
          console.log(res.data.data);
          this.chartValue = res.data.data;
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>
