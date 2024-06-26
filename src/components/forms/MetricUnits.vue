<template>
<div class="max-w-md mx-auto p-4 bg-white shadow-md rounded-md">
    <h1 class="text-2xl font-bold mb-4">BMI Calculator</h1>
    <form @submit.prevent="calculateBMI" class="space-y-4">
    <div>
        <label for="age" class="block text-sm font-medium text-gray-700">Age</label>
        <input type="number" v-model="age" id="age" class="mt-1 block w-full border-gray-300 rounded-md shadow-sm" required>
    </div>
    <div>
        <label for="gender" class="block text-sm font-medium text-gray-700">Gender</label>
        <select v-model="gender" id="gender" class="mt-1 block w-full border-gray-300 rounded-md shadow-sm" required>
        <option value="">Select Gender</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
        </select>
    </div>
    <div>
        <label for="height" class="block text-sm font-medium text-gray-700">Height (cm)</label>
        <input type="number" v-model="height" id="height" class="mt-1 block w-full border-gray-300 rounded-md shadow-sm" required>
    </div>
    <div>
        <label for="weight" class="block text-sm font-medium text-gray-700">Weight (kg)</label>
        <input type="number" v-model="weight" id="weight" class="mt-1 block w-full border-gray-300 rounded-md shadow-sm" required>
    </div>
    <button type="submit" class="w-full bg-blue-500 text-white py-2 px-4 rounded-md shadow-sm hover:bg-blue-600">Calculate BMI</button>
    </form>
    <div v-if="bmi" class="mt-4">
    <h2 class="text-xl font-bold">Your BMI: {{ bmi.toFixed(2) }}</h2>
    <p v-if="bmiCategory" class="text-sm font-medium text-gray-700">Category: {{ bmiCategory }}</p>
    </div>
</div>
</template>

<script>
export default {
data() {
    return {
    age: '',
    gender: '',
    height: '',
    weight: '',
    bmi: null,
    bmiCategory: ''
    };
},
methods: {
    calculateBMI() {
    const heightInMeters = this.height / 100;
    this.bmi = this.weight / (heightInMeters * heightInMeters);
    this.setBmiCategory();
    },
    setBmiCategory() {
    if (this.bmi < 18.5) {
        this.bmiCategory = 'Underweight';
    } else if (this.bmi >= 18.5 && this.bmi < 24.9) {
        this.bmiCategory = 'Normal weight';
    } else if (this.bmi >= 25 && this.bmi < 29.9) {
        this.bmiCategory = 'Overweight';
    } else {
        this.bmiCategory = 'Obesity';
    }
    }
}
};
</script>

<style scoped>

</style>
