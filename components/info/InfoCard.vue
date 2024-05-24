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
  <div class="w-[400px] h-[400px] rounded-lg shadow-lg p-4 flex flex-col justify-center items-center">
    <!-- Image -->
    <div class="flex-shrink-0">
      <img :src="imgSource" alt="Image" class="w-30 h-30 object-cover rounded-t-lg">
    </div>
    

    <!-- Title -->
    <div class="flex-grow flex flex-col justify-center items-center mt-4">
      <div class="mb-2">
        <h1 class="text-3xl font-sans font-semibold capitalize leading-9 font- text-center" v-html="jsonData?.title"></h1>
      </div>
    </div>

    <!-- Content -->
    <div class="w-full h-[50%] text-center">
      <p>{{ jsonData?.content }}</p>
    </div>
  </div>
</template>
