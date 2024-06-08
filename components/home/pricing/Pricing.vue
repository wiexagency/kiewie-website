<script setup>
const jsonData = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch('/data/pricing.json');
    jsonData.value = await response.json();
  } catch (error) {
    console.error('Error fetching JSON data:', error);
  }
};

onMounted(fetchData);
</script>

<template>
  <div class="w-full flex justify-center items-center mt-20">
    <div class="max-w-6xl mt-3">
      <div class="text-center">
        <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
        <h1 class="text-6xl font-bold mb-4"> {{ jsonData?.title }} </h1>
        <p> {{ jsonData?.content }} </p>
      </div>
    </div>
  </div>
  <div class="mt-20 w-4/5 mx-auto flex justify-between">
    <div v-for="bundle in jsonData?.bundles">
      <HomePricingCard :bundle></HomePricingCard>
    </div>
  </div>
</template>
