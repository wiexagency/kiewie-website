<template>
    <div class="w-full flex justify-center items-center mt-6">
        <div class="max-w-6xl">
            <div class="text-center">
                <h6 class="text-orange-600">OUR SERVICES</h6>
                <h2 class="text-5xl font-bold mb-4">Our Services</h2>
                <p class="text-lg">We specialize in lead generation and have developed our own approach and software
                    platform to efficiently and easily generate relevant leads and activate potential customers via
                    email and LinkedIn.</p>
            </div>
        </div>
    </div>
    <OrganismConnectView :order=true :service_number=1></OrganismConnectView>
    <OrganismConnectView :order=false :service_number=2></OrganismConnectView>
</template>
