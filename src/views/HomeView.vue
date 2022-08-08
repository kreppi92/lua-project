<script setup>
import LuaCard from "@/components/LuaCard.vue";
import LuaSelect from "@/components/LuaSelect.vue";
import LuaChart from "@/components/LuaChart.vue";

// import chart from '../chart.json'
import notebook from '../notebook.json'

// console.log(JSON.parse(chart[0].details))
console.log(JSON.parse(notebook[0].details))

const dataSourceOptions = Object.keys(JSON.parse(notebook[0].details).parameters)
const xAxisOptions = JSON.parse(notebook[0].details).results.meta.map(option=>option.name)
const chartTypeOptions = ["line", "bar"]

const chartType="line"
</script>

<template>
  <main>
    <LuaCard label="Cell">
      <div class="grid grid-cols-2 gap-2">
        <div>
          <LuaSelect label="Data Source" :options="dataSourceOptions" />
          <LuaSelect label="X Axis" :options="xAxisOptions" />
          <LuaSelect label="Y Axis" :options="xAxisOptions" multiple />
          <LuaSelect label="Chart Type" :options="chartTypeOptions" />
        </div>
        <div>
          <LuaChart :chartType="chartType"/>
        </div>
      </div>
    </LuaCard>
  </main>
</template>
