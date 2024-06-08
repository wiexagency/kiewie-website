<script setup>
const props = defineProps({
  order: {
    type: Boolean,
    default: true
  },
  contentSize: {
    type: String,
    default: "22px"
  },
  view: Object
});

</script>

<template>
  <div v-if="order" class="container flex items-center">
    <div class="w-1/2 flex justify-center ">
      <img :src="view?.img" alt="Image" class="w-90 h-90">
    </div>

    <div class="w-1/2 p-4">
      <h6 class="text-orange-600"> {{ view?.header }} </h6>
      <h1 class="text-6xl font-bold mb-4"> {{ view?.title }} </h1>
      <p :style="{ fontSize: contentSize }" class="font-thin" v-html="view?.content"></p>
      <button class="mt-10 bg-blue-400 hover:bg-blue-500 text-white font-bold py-3 px-6 rounded-full">
        <a :href="view?.url">{{ view?.button }}</a>
      </button>
    </div>
  </div>
  <div v-else class="container flex items-center">
    <div class="w-1/2 p-4">
      <h6 class="text-orange-600"> {{ view?.header }} </h6>
      <h1 class="text-6xl font-bold mb-4"> {{ view?.title }} </h1>
      <p :style="{ fontSize: contentSize }" class="font-thin" v-html="view?.content"></p>
      <button  class="mt-10 bg-blue-400 hover:bg-blue-500 text-white font-bold py-3 px-6 rounded-full">
        <a :href="view?.url">{{ view?.button }}</a>
      </button>    
    </div>

    <div class="w-1/2 flex justify-center">
      <img :src="view?.img" alt="Image" class="w-90 h-90">
    </div>
  </div>
</template>
  
