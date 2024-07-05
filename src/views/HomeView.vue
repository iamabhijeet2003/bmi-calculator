<template>
    <h1 class="mb-4 text-4xl font-extrabold leading-none tracking-tight text-gray-900 md:text-5xl lg:text-6xl text-center mt-6">BMI Calculator</h1>
    <div>
        <div class="mb-6 text-center">
      <button
        @click="selectedUnit = 'metric'"
        :class="{'bg-blue-500 text-white': selectedUnit === 'metric', 'bg-gray-200 text-gray-700': selectedUnit !== 'metric'}"
        class="py-2 px-4 mr-2 rounded-md focus:outline-none"
      >
        Metric Units
      </button>
      <button
        @click="selectedUnit = 'imperial'"
        :class="{'bg-blue-500 text-white': selectedUnit === 'imperial', 'bg-gray-200 text-gray-700': selectedUnit !== 'imperial'}"
        class="py-2 px-4 rounded-md focus:outline-none"
      >
        Imperial Units
      </button>
    </div>
        <div>
            <MetricUnits v-if="selectedUnit === 'metric'"></MetricUnits>
        </div>
        <div>
            <ImperialUnits v-if="selectedUnit === 'imperial'"></ImperialUnits>
        </div>
    </div>
</template>

<script>
import MetricUnits from "../components/forms/MetricUnits.vue";
import ImperialUnits from "../components/forms/ImperialUnits.vue";
export default{
    components:{
        MetricUnits,
        ImperialUnits,
    },
    data() {
    return {
      selectedUnit: 'metric',
    };
  },
}
</script>

<style>

</style>