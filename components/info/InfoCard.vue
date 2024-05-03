<script setup>
const props = defineProps({
  card_number: Number
});

const imgSource = `/images/card_icons/card-${props.card_number}.png`

const jsonData = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch(`/data/card_data/card-${props.card_number}.json`);
    jsonData.value = await response.json();
    console.log(jsonData.value);
    console.log(jsonData.value.content);
  } catch (error) {
    console.error('Error fetching JSON data:', error);
  }
};

onMounted(fetchData);
</script>

<template>
 <div class="h-90 w-1/3 bg-white rounded-lg shadow-lg p-4 flex flex-col justify-center items-center">
    <img :src="imgSource" alt="Image" class="w-48 h-48 object-cover rounded-t-lg">
    
    <h1 class="text-2xl font-bold mb-4"> {{ jsonData?.title }} </h1>
    <p class="text-center"> {{ jsonData?.content }} </p>
  </div>
</template>