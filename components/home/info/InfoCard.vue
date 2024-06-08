<script setup>
const props = defineProps({
  info_card: Object
});

</script>

<template>
  <div class="w-[400px] h-[400px] rounded-lg shadow-lg p-4 flex flex-col items-center">
    <!-- Image -->
    <div>
      <img :src="info_card?.img" alt="Image" class="w-30 h-30 object-cover rounded-t-lg">
    </div>


    <!-- Title -->
    <div class="mt-4 mb-2">
      <h1 class="text-3xl font-semibold capitalize text-center" v-html="info_card?.title">
      </h1>
    </div>

    <!-- Content -->
    <div class="w-full h-[50%] text-center font-thin">
      <p>{{ info_card?.content }}</p>
    </div>
  </div>
</template>
