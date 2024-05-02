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

// Fetch JSON data from the specified path
const fetchData = async () => {
  try {
    const response = await fetch(`/data/service-data-${props.service_number}.json`);
    jsonData.value = await response.json();
  } catch (error) {
    console.error('Error fetching JSON data:', error);
  }
};

// Fetch the data when the component is mounted
onMounted(fetchData);

</script>

<template>
  <div v-if="order" class="container mx-auto flex justify-center items-center">
    <!-- Image (left side) -->
    <div class="w-1/2 flex justify-center items-center">
      <img :src="imgSource" alt="Image" class="w-64 h-auto">
    </div>

    <!-- Text (right side) -->
    <div class="w-1/2 p-4">
      <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
      <h1 class="text-6xl font-bold mb-4"> {{ jsonData?.title }} </h1>
      <p> {{ jsonData?.content }} </p>      
    </div>
  </div>
  <div v-else class="container mx-auto flex justify-center items-center">
    <div class="w-1/2 p-4">
      <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
      <h1 class="text-6xl font-bold mb-4"> {{ jsonData?.title }} </h1>
      <p> {{ jsonData?.content }} </p>      
    </div>

    <div class="w-1/2 flex justify-center items-center">
      <img :src="imgSource" alt="Image" class="w-64 h-auto">
    </div>
  </div>
</template>
  
