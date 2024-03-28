<script>
import SelectNumber from './components/SelectNumber.vue'

export default {
  components: {
    SelectNumber
  },
}

</script>

<template>

  <div class="flex flex-col justify-start items-center min-h-screen bg-red-200 py-6">
    <h1 class="text-4xl font-bold">Guess the number</h1>
    <p class="mt-4 font-bold text-2xl">Number between 1 and 100 has been selected</p>

    <SelectNumber class="pt-6" />

  </div>

</template>