<script setup>
defineProps({
  label: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <div class="bg-gray-800 sm:px-0">
    <div
      class="border border-solid border-b-0 border-gray-600 px-6 h-10 text-white flex items-center font-bold"
    >
      {{ label }}
    </div>
    <div class="border border-solid border-gray-600 px-6 pb-6">
      <slot />
    </div>
  </div>
</template>
