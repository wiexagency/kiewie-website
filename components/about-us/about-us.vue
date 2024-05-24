<script setup>
import ConnectView from '~/organism/ConnectView.vue';

const imageSrc = '/images/hero-img.png';

const jsonData = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch('/data/about-us.json');
    jsonData.value = await response.json();
    console.log(jsonData.value);
  } catch (error) {
    console.error('Error fetching JSON data:', error);
  }
};

onMounted(fetchData);
</script>

<template>
  <ConnectView :view="jsonData"></ConnectView>
</template>
