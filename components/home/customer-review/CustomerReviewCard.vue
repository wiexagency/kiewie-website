<script setup>
const props = defineProps({
  review: Object
});

</script>

<template>
  <div class="w-[400px] h-[350px] rounded-lg shadow-lg flex flex-col p-4">
    <div>
      <div class="flex">
        <!-- Customer image -->
        <div class="mr-4">
          <img :src="review?.img" alt="Image" class="w-14 h-14 object-cover rounded-t-lg">
        </div>

        <!-- Customer info -->
        <div class="flex flex-col">
          <div>
            <h1 class="text-lg font-sans font-semibold capitalize">{{ review?.name }}</h1>
            <p class="text-xs font-thin capitalize ">{{ review?.position }} at {{ review?.company }}</p>
          </div>
        </div>
      </div>
      <!-- Review -->
      <div class="mb-2">
        <p class=" font-thin">“{{ review?.review }}”</p>
      </div>
    </div>

    <!-- Rating -->
    <div class="mt-auto">
      <div :style="{ backgroundColor: '#F1FBFF' }" class="flex rounded justify-between py-2 px-2">
        <div>
          <p>Rated ({{ review?.rating }} of 5)</p>
        </div>
        <div>
          <span v-for="index in 5" :key="index">
            <i v-if="index <= review?.rating" class="text-blue-400">&#9733;</i>
            <i v-else class="text-gray-300">&#9733;</i>
          </span>
        </div>
      </div>
    </div>
  </div>
</template>
