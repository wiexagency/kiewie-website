<template>
  <div class="container mx-auto flex justify-between justify-center items-center">
    <!-- Text on the left -->
    <div class="w-1/2 ">
      <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
      <h1 class="text-6xl font-bold mb-4"> {{ jsonData?.title }} </h1>
      <p> {{ jsonData?.content }} </p>
    </div>

    <!-- Image on the right -->
    <div class="w-1/2 p-4">
      <img :src="imageSrc" alt="Image" class="w-full h-auto">
    </div>
  </div>
</template>
  
  <script setup>
  // Define the image source
  const imageSrc = '/images/hero-img.png';

// Define a ref to hold the fetched JSON data
const jsonData = ref(null);

// Fetch JSON data from the specified path
const fetchData = async () => {
  try {
    const response = await fetch('/data/mainPage.json');
    jsonData.value = await response.json();
  } catch (error) {
    console.error('Error fetching JSON data:', error);
  }
};

// Fetch the data when the component is mounted
onMounted(fetchData);

  </script>

  