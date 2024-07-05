<template>
    <div class="max-w-md mx-auto p-4 bg-white shadow-md rounded-md">
      <form @submit.prevent="calculateBMI" class="space-y-4">
        <div>
          <label for="age" class="mb-3 block text-base font-medium text-[#07074D]">Age</label>
          <input type="number"
                 v-model="age"
                 id="age"
                 class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
                 required
                 min="1"
                 max="120"
          >
        </div>
        <div>
          <label for="gender" class="mb-3 block text-base font-medium text-[#07074D]">Gender</label>
          <select v-model="gender" id="gender" class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md" required>
            <option value="">Select Gender</option>
            <option value="male">Male</option>
            <option value="female">Female</option>
          </select>
        </div>
        <div class="flex space-x-4">
        <div class="flex-1">
          <label for="heightFeet" class="mb-3 block text-base font-medium text-[#07074D]">Height (feet)</label>
          <input type="number"
                 v-model="heightFeet"
                 id="heightFeet"
                 class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
                 required
                 min="1"
                 max="8"
          >
        </div>
        <div class="flex-1">
          <label for="heightInches" class="mb-3 block text-base font-medium text-[#07074D]">Height (inches)</label>
          <input type="number"
                 v-model="heightInches"
                 id="heightInches"
                 class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
                 required
                 min="0"
                 max="11"
          >
        </div>
      </div>
        <div>
          <label for="weight" class="mb-3 block text-base font-medium text-[#07074D]">Weight (lbs)</label>
          <input type="number"
                 v-model="weight"
                 id="weight"
                 class="w-full rounded-md border border-[#e0e0e0] bg-white py-3 px-6 text-base font-medium text-[#6B7280] outline-none focus:border-[#6A64F1] focus:shadow-md"
                 required
                 min="5"
          >
        </div>
        <button type="submit" class="hover:shadow-form w-full rounded-md bg-[#6A64F1] py-3 px-8 text-center text-base font-semibold text-white outline-none">Calculate BMI</button>
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
        heightFeet: '',
        heightInches: '',
        weight: '',
        bmi: null,
        bmiCategory: ''
      };
    },
    methods: {
      calculateBMI() {
        const heightInInches = (this.heightFeet * 12) + parseFloat(this.heightInches);
        const heightInMeters = heightInInches * 0.0254;
        const weightInKg = this.weight * 0.453592;
        this.bmi = weightInKg / (heightInMeters * heightInMeters);
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
  