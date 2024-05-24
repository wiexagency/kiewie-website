<script setup>
import ConnectView from '~/organism/ConnectView.vue';

const imageSrc = '/images/hero-img.png';

const jsonData = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch('/data/service_data/service-page.json');
    jsonData.value = await response.json();
  } catch (error) {
    console.error('Error fetching JSON data:', error);
  }
};

onMounted(fetchData);
</script>

<template>
    <div class="w-full flex justify-center items-center mt-6">
        <div class="max-w-6xl">
            <div class="text-center">
                <h6 class="text-orange-600"> {{ jsonData?.header }} </h6>
                <h1 class="text-6xl font-bold mb-4"> {{ jsonData?.title }} </h1>
                <p> {{ jsonData?.content }} </p>
            </div>
        </div>
    </div>
    <div v-for="service in jsonData?.services">
      <ConnectView :order=service?.order :service="service"></ConnectView>
    </div>
</template>
