<template>
  <v-chart class="chart" :option="option" />
</template>

<script>
import { use } from "echarts/core";
import { CanvasRenderer } from "echarts/renderers";
import { PieChart, BarChart, LineChart } from "echarts/charts";
import { GridComponent, TooltipComponent } from "echarts/components";
import VChart from "vue-echarts";
import { ref, defineComponent } from "vue";
import chart from "../chart.json";

use([
  CanvasRenderer,
  BarChart,
  LineChart,
  GridComponent,
  TooltipComponent,
  PieChart,
]);

export default defineComponent({
  name: "HelloWorld",
  components: {
    VChart,
  },
  setup() {
    const option = JSON.parse(chart[0].details).viz.eChart;
    // const option = ref({
    //   xAxis: { type: "category" },
    //   yAxis: {
    //     show: false,
    //   },
    //   series: [
    //     {
    //       name: "Traffic Sources",
    //       type: "line",
    //       data: randomValues,
    //       emphasis: {
    //         itemStyle: {
    //           shadowBlur: 10,
    //           shadowOffsetX: 0,
    //           shadowColor: "rgba(0, 0, 0, 0.5)",
    //         },
    //       },
    //     },
    //     {
    //       name: "Traffic Sources 2",
    //       type: "line",
    //       data: randomValues.map((i) => i * 2),
    //       emphasis: {
    //         itemStyle: {
    //           shadowBlur: 10,
    //           shadowOffsetX: 0,
    //           shadowColor: "rgba(0, 0, 0, 0.5)",
    //         },
    //       },
    //     },
    //     {
    //       name: "Traffic Sources",
    //       type: "bar",
    //       data: randomValues.map((i) => i / 3),
    //       emphasis: {
    //         itemStyle: {
    //           shadowBlur: 10,
    //           shadowOffsetX: 0,
    //           shadowColor: "rgba(0, 0, 0, 0.5)",
    //         },
    //       },
    //     },
    //   ],
    // });

    return { option };
  },
});
</script>

<style scoped>
.chart {
  height: 350px;
}
</style>
