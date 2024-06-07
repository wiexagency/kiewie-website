<template>
    <div class="bg-white py-4 border-b container mx-auto flex justify-between items-center">
      <div>
        <img src="/images/logo.png" alt="Kiwi Logo" class="h-10" />
      </div>

      <nav class="text-center">
        <ul class="flex justify-center space-x-6">
          <li><NuxtLink to="/" class="cursor-pointer hover:text-orange-300">Home</NuxtLink></li>
          <li><NuxtLink to="/services" class="cursor-pointer hover:text-orange-300">Services</NuxtLink></li>
          <li><NuxtLink to="/why-us" class="cursor-pointer hover:text-orange-300">Why us?</NuxtLink></li>
          <li><NuxtLink to="/review" class="cursor-pointer hover:text-orange-300">Review</NuxtLink></li>
          <li><NuxtLink to="/who-are-we" class="cursor-pointer hover:text-orange-300">Who are we?</NuxtLink></li>
          <li><NuxtLink to="/contact" class="cursor-pointer hover:text-orange-300">Contact</NuxtLink></li>
        </ul>
      </nav>

      <div>
        <button class="bg-blue-400 hover:bg-blue-500 text-white font-bold py-3 px-6 rounded-full">
          Try a monthly trial ->
        </button>
      </div>
    </div>
</template>

<script setup>
</script>
