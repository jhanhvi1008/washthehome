<template>
  <div class="min-h-screen bg-gray-100 flex items-center justify-center">
    <div v-if="step === 1">
      <QuoteForm :formData="formData" @update-form-data="updateFormData" @next-step="step = 2"/>
    </div>
    <div v-else-if="step === 2">
      <QuoteSummary :formData="formData"/>
    </div>
  </div>
</template>

<script>
import QuoteForm from './components/QuoteForm.vue'
import QuoteSummary from './components/QuoteSummary.vue'

export default {
  components: {
    QuoteForm,
    QuoteSummary
  },
  data() {
    return {
      step: 1,
      formData: {
        service: 'cleaning',
        date: '',
        time: ''
      }
    };
  },
  methods: {
    updateFormData(newData) {
      this.formData = newData; // Update formData with new data from child component
    }
  }
}
</script>

<style>
body {
  @apply bg-gray-100;
}
</style>
