<script setup>
const props = defineProps({
    bundle: Object
});

</script>
<template>
    <div style="height: 450px;" class="w-[400px] rounded-lg shadow-lg flex flex-col justify-between items-center p-4">
        <div class="flex-grow">
            <div class="mb-4 flex flex-row w-full">
                <div>
                    <img :src="bundle?.img" alt="Image" class="w-8 h-8 object-cover rounded-t-lg">
                </div>
            </div>

            <div class="mb-2">
                <h1 class="text-3xl font-bold">{{ bundle?.type }}</h1>
            </div>

            <div class="mb-2">
                <p class="font-thin">{{ bundle?.shortDescription }}</p>
            </div>

            <div class="text-lg font-bold">
                {{ bundle?.pricing }} PER MONTH /
                <br>
                {{ bundle?.leads }} LEADS PER MONTH
            </div>

            <ul v-for="detail in bundle?.details" :key="detail">
                <li style="list-style-type: square; margin-left: 20px;">{{ detail }}</li>
            </ul>
        </div>

        <button class="w-full mt-10 bg-blue-400 hover:bg-blue-500 text-white font-bold py-3 px-6 rounded-full">
            <a :href="bundle?.url" class="block text-center w-full h-full">{{ bundle?.button }}</a>
        </button>

    </div>
</template>