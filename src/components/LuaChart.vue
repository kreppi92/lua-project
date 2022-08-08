<template>
  <v-chart class="chart" :option="option" />
</template>

<script setup>
import { use } from "echarts/core";
import { CanvasRenderer } from "echarts/renderers";
import { PieChart, BarChart, LineChart } from "echarts/charts";
import { GridComponent, TooltipComponent } from "echarts/components";
import VChart from "vue-echarts";
import { ref, toRefs } from "vue";
import chart from "../chart.json";

use([
  CanvasRenderer,
  BarChart,
  LineChart,
  GridComponent,
  TooltipComponent,
  PieChart,
]);


const props = defineProps({
  chartType: {
    type: String
  }
})

const { chartType } = toRefs(props);
const response = JSON.parse(chart[0].details).viz.eChart
response.series[0].type = chartType.value
console.log(response)
const option = ref(response)
</script>

<style scoped>
.chart {
  height: 350px;
}
</style>
