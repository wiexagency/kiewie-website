<script setup>
const props = defineProps({
  card_number: Number
});

const imgSource = `/images/customer_icons/customer_card-${props.card_number}.png`

const jsonData = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch(`/data/customer_data/customer_card-${props.card_number}.json`);
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
  <div class="w-[400px] h-[350px] rounded-lg shadow-lg flex flex-col justify-between items-center p-4">
    <div>
      <div class="flex flex-row w-full mb-auto">
        <!-- Customer image -->
        <div class="mr-4">
          <img :src="imgSource" alt="Image" class="w-14 h-14 object-cover rounded-t-lg">
        </div>

        <!-- Customer info -->
        <div class="flex flex-col">
          <div>
            <h1 class="text-lg font-sans font-semibold capitalize">{{ jsonData?.name }}</h1>
            <p class="text-xs font-thin capitalize ">{{ jsonData?.position }} at {{ jsonData?.company }}</p>
          </div>
        </div>
      </div>
      <!-- Review -->
      <div class="mb-2">
        <p class=" font-thin">“{{ jsonData?.review }}”</p>
      </div>
    </div>

    <!-- Rating -->
    <div class="w-full mt-auto">
      <div class="flex items-center bg-blue-100 justify-between py-2 px-2">
        <div>
          <p>Rated ({{ jsonData?.rating }} of 5)</p>
        </div>
        <div>
          <span v-for="index in 5" :key="index">
            <i v-if="index <= jsonData?.rating" class="text-blue-400">&#9733;</i>
            <i v-else class="text-gray-300">&#9733;</i>
          </span>
        </div>
      </div>
    </div>
  </div>
</template>
