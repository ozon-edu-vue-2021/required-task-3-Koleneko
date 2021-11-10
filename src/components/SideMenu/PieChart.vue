<template><PieChart ref="chart" /></template>

<script>
import { Doughnut } from "vue-chartjs";

export default {
  components: {
    PieChart: Doughnut,
  },
  props: {
    legend: [],
  },
  mounted() {
    this.makeChart();
  },
  methods: {
    makeChart() {
      const legendChartData = {
        labels: this.legend.map((it) => it.text),
        datasets: [
          {
            label: "Легенда",
            backgroundColor: this.legend.map((legendItem) => legendItem.color),
            data: this.legend.map((legendItem) => legendItem.counter),
          },
        ],
      };
      const options = {};
      this.$refs.chart.renderChart(legendChartData, options);
    },
  },
};
</script>

<style scoped></style>
