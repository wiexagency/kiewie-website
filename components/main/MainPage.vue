<template>
  <div class="container mx-auto flex justify-between justify-center items-center">
    <div class="w-1/2 max-w-lg ">
      <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
      <h1 class="text-6xl font-bold mb-4"> {{ jsonData?.title }} </h1>
      <p> {{ jsonData?.content }} </p>
    </div>

    <div class="w-1/2 p-4">
      <img :src="imageSrc" alt="Image" class="w-full h-auto">
    </div>
  </div>
</template>

<script setup>
const imageSrc = '/images/hero-img.png';

const jsonData = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch('/data/mainPage.json');
    jsonData.value = await response.json();
  } catch (error) {
    console.error('Error fetching JSON data:', error);
  }
};

onMounted(fetchData);
</script>