<script setup>
const props = defineProps({
  order: {
    type: Boolean,
    default: true
  },
  service_number: Number
});

const imgSource = `/images/service-img-${props.service_number}.png`

const jsonData = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch(`/data/service-data-${props.service_number}.json`);
    jsonData.value = await response.json();
  } catch (error) {
    console.error('Error fetching JSON data:', error);
  }
};

onMounted(fetchData);

</script>

<template>
  <div v-if="order" class="container mx-auto flex justify-center items-center">
    <div class="w-1/2 flex justify-center items-center">
      <img :src="imgSource" alt="Image" class="w-90 h-90">
    </div>

    <div class="w-1/2 p-4">
      <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
      <h1 class="text-6xl font-bold mb-4"> {{ jsonData?.title }} </h1>
      <p> {{ jsonData?.content }} </p>
      <button class="mt-7 bg-blue-400 hover:bg-blue-500 text-white font-bold py-3 px-6 rounded-full">
        Read More ->
      </button>
    </div>
  </div>
  <div v-else class="container mx-auto flex justify-center items-center">
    <div class="w-1/2 p-4">
      <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
      <h1 class="text-6xl font-bold mb-4"> {{ jsonData?.title }} </h1>
      <p> {{ jsonData?.content }} </p>
      <button class="mt-7 bg-blue-400 hover:bg-blue-500 text-white font-bold py-3 px-6 rounded-full">
        Read More ->
      </button>    
    </div>

    <div class="w-1/2 flex justify-center items-center">
      <img :src="imgSource" alt="Image" class="w-90 h-90">
    </div>
  </div>
</template>
  
