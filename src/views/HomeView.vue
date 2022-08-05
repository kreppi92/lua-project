<script setup>
import LuaCard from "@/components/LuaCard.vue";
import LuaSelect from "@/components/LuaSelect.vue";
import LuaChart from "@/components/LuaChart.vue";
</script>

<template>
  <main>
    <LuaCard label="Cell">
      <div class="grid grid-cols-2 gap-2">
        <div>
          <LuaSelect label="Data Source" />
          <LuaSelect label="X Axis" />
          <LuaSelect label="Y Axis" />
          <LuaSelect label="Chart Type" />
        </div>
        <div>
          <LuaChart />
        </div>
      </div>
    </LuaCard>
  </main>
</template>
