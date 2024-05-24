<script setup>
const props = defineProps({
  order: {
    type: Boolean,
    default: true
  },
  service_number: Number
});

const imgSource = `/images/trail-banner.png`

const jsonData = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch(`/data/trail-banner.json`);
    jsonData.value = await response.json();
  } catch (error) {
    console.error('Error fetching JSON data:', error);
  }
};

onMounted(fetchData);

</script>

<template>
  <div class="container mx-auto flex justify-center items-center text-white rounded-3xl mt-40" style="background-color: #00003C;">
    <div class="w-1/2 p-4">
      <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
      <h1 class="text-6xl font-bold mb-4" v-html="jsonData?.title"></h1>
      <p> {{ jsonData?.content }} </p>
      <button @click="" class="mt-10 bg-blue-400 hover:bg-blue-500 text-white font-bold py-3 px-6 rounded-full">
        <a :href="jsonData?.buttonLink"> {{ jsonData?.buttonText }}</a>
      </button>
    </div>

    <div class="w-1/2 flex justify-center items-center rounded">
      <img :src="imgSource" alt="Image" class="bg-blue-300 w-90 h-90 rounded-t-md">
    </div>
  </div>
</template>
  
