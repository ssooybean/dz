<script setup>
import axios from 'axios';
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from 'chart.js';
import { Bar } from 'vue-chartjs';
</script>

<template>
  <section>
    <div><Bar :data="data" :options="options" /></div>
  </section>
</template>

<script>
ChartJS.register(CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend);
export default {
  components: {
    Bar,
  },
  props: {
    req: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      data: {
        labels: [...new Array(this.req.length).map((_, i) => (_ = i + 1))],
        datasets: [{ data: [...this.req.filter((n) => n.max_temp)] }],
      },
      options: {
        responsive: true,
      },
    };
  },
  mounted() {
    axios
      .get(
        `https://api.weatherbit.io/v2.0/history/daily?city=${this.req.city}&start_date=${this.req.from}&end_date=${this.req.to}&key=3549b3f6bfdb4cf6a5fa7318b057dfd0`,
      )
      .then((res) => console.log(res.data.data))
      .catch(function (error) {
        console.log(error);
      });
  },
  methods: {},
};
</script>
