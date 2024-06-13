<template>
  <div class="p-4 max-w-md mx-auto bg-white shadow-md rounded-md">
    <h2 class="text-xl font-semibold mb-4">Your Quote</h2>
    <p><strong>Service Type:</strong> {{ formData.service }}</p>
    <p><strong>Date:</strong> {{ formData.date }}</p>
    <p><strong>Time:</strong> {{ formData.time }}</p>
    <div class="mt-4">
      <button @click="getQuote" class="w-full bg-indigo-600 text-white py-2 px-4 rounded-md shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">Get Quote</button>
    </div>
    <div v-if="quote" class="mt-4 bg-gray-100 p-4 rounded-md">
      <p><strong>Estimated Price:</strong> ${{ quote.price }}</p>
      <a :href="quote.pdfUrl" target="_blank" class="text-indigo-600 hover:underline">Download PDF</a>
    </div>
  </div>
</template>

<script>
export default {
  props: ['formData'],
  data() {
    return {
      quote: null
    };
  },
  methods: {
    async getQuote() {
      // Simulate API call
      this.quote = {
        price: (Math.random() * 100).toFixed(2),
        pdfUrl: '/path/to/quote.pdf'
      };
    }
  }
}
</script>
