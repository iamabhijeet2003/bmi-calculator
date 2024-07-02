<template>
    <h1 class="mb-4 text-4xl font-extrabold leading-none tracking-tight text-gray-900 md:text-5xl lg:text-6xl text-center mt-6">BMI Calculator</h1>
    <div>
        <h2 class="text-4xl font-extrabold text-center">Metric Units</h2>
        <div>
            <MetricUnits></MetricUnits>
        </div>
    </div>
</template>

<script>
import MetricUnits from "../components/forms/MetricUnits.vue";

export default{
    components:{
        MetricUnits
    }
}
</script>

<style>

</style>