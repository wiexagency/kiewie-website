<script setup>
import CustomerReviewCard from './CustomerReviewCard.vue';

const jsonData = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch('/data/customer_data/CustomerPage.json');
    jsonData.value = await response.json();
  } catch (error) {
    console.error('Error fetching JSON data:', error);
  }
};

onMounted(fetchData);
</script>

<template>
  <div class="flex justify-center mt-20">
    <div>
      <div class="text-center">
        <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
        <h1 class="text-6xl font-bold mb-4"> {{ jsonData?.title }} </h1>
        <p> {{ jsonData?.content }} </p>
      </div>
    </div>
  </div>
  <div class="mt-20 w-4/5 mx-auto flex justify-between">
    <div v-for="review in jsonData?.reviews">
      <CustomerReviewCard :review="review"></CustomerReviewCard>
    </div>
  </div>
</template>