<template>
    <footer class="bg-blue-100 py-10 border-t mt-10">
        <div class="container mx-auto flex justify-between items-start">
            <!-- Section 1: Large Kiwi text -->
            <FooterMain/>

            <!-- Section 2: Company with links -->
            <FooterCompany/>

            <!-- Section 3: Help center -->
            <FooterHelpCenter/>

            <!-- Section 4: Contact info -->
            <FooterContactInfo/>
        </div>

        <!-- Horizontal line -->
        <div class="container mx-auto my-6 border-t border-gray-300"></div>

        <!-- Section 5: Copyright and Section 6: News, Media kit, Press -->
        <div class="container mx-auto flex justify-between items-center text-gray-500">
            <p>&copy; 2024 <span class="text-blue-500">Kiewie</span>. All rights reserved.</p>
            <FooterResources/>
        </div>
    </footer>
</template>

<script setup>

</script>