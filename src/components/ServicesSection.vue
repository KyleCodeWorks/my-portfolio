<template>
    <section class="mt-20" id="services">
        <div class="px-4 xl:pl-16">
            <h2 class="text-4xl font-bold mb-4">My
                <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">Services</span>
            </h2>
        </div>
        <div class="py-8 px-4 xl:px-16 grid grid-cols-1 gap-6 sm:grid-cols-2 md:gap-8 md:grid-cols-2">
            <div v-for="service in services" :key="service.id" data-aos="fade-up"
                class="card bg-base-100 shadow-lg hover:shadow-xl transition-shadow duration-300 ease-in-out p-6 flex flex-col items-center text-center">
                <!-- Service Icon -->
                <figure class="h-24 w-24 xl:h-28 xl:w-28 mb-4">
                    <div v-html="service.icon" class="rounded-xl"></div>
                </figure>
                <!-- Service Details -->
                <div class="card-body items-center text-center">
                    <!-- Title -->
                    <h2 class="card-title text-xl font-bold">{{ service.name }}</h2>
                    <!-- Description -->
                    <p class="font-normal mt-2">{{ service.description }}</p>
                </div>
            </div>
        </div>
    </section>
</template>
<script setup>
import { ref } from 'vue';
const services = ref([
    {
        id: 1,
        icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="h-full w-full">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M7.5 14.25v2.25m3-4.5v4.5m3-6.75v6.75m3-9v9M6 20.25h12A2.25 2.25 0 0 0 20.25 18V6A2.25 2.25 0 0 0 18 3.75H6A2.25 2.25 0 0 0 3.75 6v12A2.25 2.25 0 0 0 6 20.25Z" />
                </svg>`,
        name: 'Data Analytics & Visualization',
        description: "Provides comprehensive solutions for cleaning, transforming, and analyzing data to uncover valuable insights. Expertise in creating visually compelling dashboards and reports using advanced data visualization techniques and web development libraries. These solutions facilitate better understanding and communication of complex data, enabling businesses to make data-driven decisions and achieve their strategic goals.",
    },
    {
        id: 2,
        icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="h-full w-full">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M14.25 9.75 16.5 12l-2.25 2.25m-4.5 0L7.5 12l2.25-2.25M6 20.25h12A2.25 2.25 0 0 0 20.25 18V6A2.25 2.25 0 0 0 18 3.75H6A2.25 2.25 0 0 0 3.75 6v12A2.25 2.25 0 0 0 6 20.25Z" />
                </svg>`,
        name: 'Back-End Development & API Integration',
        description: "Delivers reliable and efficient backend systems tailored to support various web applications. Specializes in PHP development, focusing on API creation, database integration, and ensuring secure and seamless functionality. Responsibilities include maintaining system performance, optimizing processes, and enabling smooth integration with front-end components to meet the needs of dynamic projects.",
    },
    {
        id: 3,
        icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="h-full w-full">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M20.25 6.375c0 2.278-3.694 4.125-8.25 4.125S3.75 8.653 3.75 6.375m16.5 0c0-2.278-3.694-4.125-8.25-4.125S3.75 4.097 3.75 6.375m16.5 0v11.25c0 2.278-3.694 4.125-8.25 4.125s-8.25-1.847-8.25-4.125V6.375m16.5 0v3.75m-16.5-3.75v3.75m16.5 0v3.75C20.25 16.153 16.556 18 12 18s-8.25-1.847-8.25-4.125v-3.75m16.5 0c0 2.278-3.694 4.125-8.25 4.125s-8.25-1.847-8.25-4.125" />
                </svg>`,
        name: 'SQL Database Design & Optimization',
        description: "Offers expertise in MSSQL, MySQL, and database scripting to design, maintain, and optimize database systems. Responsibilities include creating robust data models, developing efficient queries, and ensuring consistent database performance. This expertise supports efficient data storage, retrieval, and analysis, enabling businesses to manage their data assets effectively and support operational success.",
    },
    {
        id: 4,
        icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="h-full w-full">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 6h9.75M10.5 6a1.5 1.5 0 1 1-3 0m3 0a1.5 1.5 0 1 0-3 0M3.75 6H7.5m3 12h9.75m-9.75 0a1.5 1.5 0 0 1-3 0m3 0a1.5 1.5 0 0 0-3 0m-3.75 0H7.5m9-6h3.75m-3.75 0a1.5 1.5 0 0 1-3 0m3 0a1.5 1.5 0 0 0-3 0m-9.75 0h9.75" />
                </svg>`,
        name: 'Excel & VBA Automation Solutions',
        description: "Develops customized automation solutions using Excel VBA to streamline repetitive tasks and enhance workflow efficiency. Responsibilities include designing macros, creating user-friendly interfaces, and ensuring the reliability of automated processes. These solutions focus on reducing errors, saving time, and improving productivity, ultimately empowering businesses to operate more effectively.",
    },
])


</script>
