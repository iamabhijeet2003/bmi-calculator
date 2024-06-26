<template>
    <h1>BMI Calculator</h1>
    <div>
        <h2>Metric Units</h2>
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