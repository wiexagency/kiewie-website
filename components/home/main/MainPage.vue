<script setup>
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

<template>
  <div class="flex justify-center items-center">
    <div class="max-w-lg">
      <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
      <h1 class="text-6xl font-bold mb-4"> {{ jsonData?.title }} </h1>
      <p> {{ jsonData?.content }} </p>
      <button class="mt-10 bg-blue-400 hover:bg-blue-500 text-white font-bold py-3 px-6 rounded-full">
        <a :href="jsonData?.buttonLink"> {{ jsonData?.buttonText }}</a>
      </button>
    </div>

    <div>
      <img :src="jsonData?.img" alt="Image" class="w-full h-auto">
    </div>
  </div>
</template>