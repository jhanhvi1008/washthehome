<template>
  <div class="p-4 max-w-md mx-auto bg-white shadow-md rounded-md">
    <h2 class="text-xl font-semibold mb-4">Get an Instant Quote</h2>
    <form @submit.prevent="nextStep">
      <div class="mb-4">
        <label for="service" class="block text-sm font-medium text-gray-700">Service Type</label>
        <select id="service" v-model="localFormData.service" class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm">
          <option value="cleaning">Cleaning</option>
          <option value="repair">Repair</option>
          <option value="installation">Installation</option>
        </select>
      </div>
      <div class="mb-4">
        <label for="date" class="block text-sm font-medium text-gray-700">Date</label>
        <input type="date" id="date" v-model="localFormData.date" class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" required>
      </div>
      <div class="mb-4">
        <label for="time" class="block text-sm font-medium text-gray-700">Time</label>
        <input type="time" id="time" v-model="localFormData.time" class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" required>
      </div>
      <button type="submit" class="w-full bg-indigo-600 text-white py-2 px-4 rounded-md shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">Next</button>
    </form>
  </div>
</template>

<script>
export default {
  props: ['formData'],
  data() {
    return {
      localFormData: { ...this.formData } // Create a local copy of formData
    };
  },
  methods: {
    nextStep() {
      this.$emit('update-form-data', this.localFormData); // Emit event to update parent component's formData
      this.$emit('next-step');
    }
  }
}
</script>
