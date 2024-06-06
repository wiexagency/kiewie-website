<script setup>
const props = defineProps({
  info_card: Object
});

</script>

<template>
  <div class="w-[400px] h-[400px] rounded-lg shadow-lg p-4 flex flex-col justify-center items-center">
    <!-- Image -->
    <div class="flex-shrink-0">
      <img :src="info_card?.img" alt="Image" class="w-30 h-30 object-cover rounded-t-lg">
    </div>
    

    <!-- Title -->
    <div class="flex-grow flex flex-col justify-center items-center mt-4">
      <div class="mb-2">
        <h1 class="text-3xl font-sans font-semibold capitalize leading-9 font- text-center" v-html="info_card?.title"></h1>
      </div>
    </div>

    <!-- Content -->
    <div class="w-full h-[50%] text-center font-thin">
      <p>{{ info_card?.content }}</p>
    </div>
  </div>
</template>
