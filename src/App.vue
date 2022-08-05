<script setup>
import { RouterLink, RouterView } from "vue-router";
// import chart from './chart.json'
import notebook from './notebook.json'

// console.log(JSON.parse(chart[0].details))
console.log(JSON.parse(notebook[0].details))
</script>

<template>
  <div class="min-h-full">
    <!-- Navbar - move to separate component -->
    <nav class="bg-gray-800">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-16">
          <div class="flex items-center">
            <div class="hidden md:block">
              <div class="ml-10 flex items-baseline space-x-4">
                <!-- Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white" -->
                <RouterLink
                  to="/"
                  class="bg-gray-900 text-white px-3 py-2 rounded-md text-sm font-medium"
                  aria-current="page"
                  >Home</RouterLink
                >
                <RouterLink
                  to="/about"
                  class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium"
                  >About</RouterLink
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </nav>
    <!-- navbar end -->

    <main>
      <div class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        <RouterView />
      </div>
    </main>
  </div>
</template>
