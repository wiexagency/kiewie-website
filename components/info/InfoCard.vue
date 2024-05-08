<script setup>
const props = defineProps({
  card_number: Number
});

const imgSource = `/images/card_icons/info_card-${props.card_number}.png`

const jsonData = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch(`/data/card_data/info_card-${props.card_number}.json`);
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
  <div class="w-[400px] h-[350px] bg-white rounded-lg shadow-lg p-4 flex flex-col justify-center items-center">
    <!-- Image -->
    <div class="flex-shrink-0">
      <img :src="imgSource" alt="Image" class="w-40 h-40 object-cover rounded-t-lg">
    </div>
    
    <!-- Content -->
    <div class="flex-grow flex flex-col justify-center items-center mt-4">
      <h1 class="text-2xl font-bold mb-2 text-center">{{ jsonData?.title }}</h1>
      <p class="text-center">{{ jsonData?.content }}</p>
    </div>
  </div>
</template>
