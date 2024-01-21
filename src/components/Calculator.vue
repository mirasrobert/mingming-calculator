<template>
  <div
    class="mx-auto block p-6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
    <form class="mx-auto">
      <div class="mb-5">
        <label
          for="hours"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Hours</label
        >

        <input
          v-model.number="hours"
          type="number"
          id="hours"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 mb-3"
          placeholder="Input your hour usage"
          required />
      </div>

      <div class="mb-5">
        <label
          for="number"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Minutes</label
        >

        <input
          v-model.number="minutes"
          type="minutes"
          id="minutes"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 mb-3"
          placeholder="Input your minute usage"
          required />
        <hr />
        <div class="flex justify-end mt-5">
          <h1 class="text-white text-3xl">&#8369; {{ calculateTotalUsage }}</h1>
        </div>
      </div>
    </form>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'

const minutes = ref(null)
const hours = ref(null)

const calculateTotalUsage = computed(() => {
  const sixtyMin = 60
  const hourToMin = hours.value * sixtyMin
  const totalMinuteUsage = hourToMin + minutes.value
  const costPerMinute = 3.2

  const totalCost = parseFloat(totalMinuteUsage) / parseFloat(costPerMinute)

  return Math.round(parseFloat(totalCost)) || 0
})
</script>
