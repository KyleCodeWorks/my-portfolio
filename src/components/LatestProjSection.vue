<template>
    <section class="mt-20" id="projects">
        <div class="px-4 xl:pl-16">
            <div class="mb-4 md:flex md:justify-between xl:pr-16">
                <h2 class="text-4xl font-bold">My
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">Latest Projects</span>
                </h2>
                <div class="flex space-x-4 mb-4 mt-5 md:mt-0">
                    <button class="hover:text-primary cursor-pointer" v-for="category in ['All', 'Web Development', 'Mobile App']"
                        :key="category" @click="() => selectedCategory = category">
                        {{ category }}
                    </button>
                </div>
            </div>
            <ul class="px-4 sm:py-16 xl:pr-16 grid grid-cols-1 gap-6 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3"
                data-aos="fade-right">
                <div v-for="project in filteredProjects" :key="project.id">
                    <div class="relative group">
                        <img :src="project.images[0]" class="w-full h-52 md:h-[24rem] rounded-t-xl object-cover transition-opacity duration-300 group-hover:opacity-75" />
                        <button class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300" @click="openModal(project)">
                            <span class="text-2xl">🔍</span>
                        </button>
                    </div>
                    <div class="rounded-b-xl mt-3 bg-base-100 shadow-lg py-6 px-4">
                        <h3 class="text-lg font-semibold uppercase lg:text-xl"> {{ project.title }}</h3>
                        <p>{{ truncateDescription(project.description) }} <span v-if="project.description.split(' ').length > 20" class="text-primary cursor-pointer" @click="openModal(project)">(read more)</span></p>
                        <div class="flex flex-wrap p-2.5">
                            <div v-for="technology in project.technologies" :key="technology"
                                class="text-center ml-1 mt-1 rounded-3xl bg-base-200 backdrop-blur-md">
                                <span class="px-2 py-2 badge badge-md badge-info">{{ technology }}</span>
                            </div>
                        </div>
                    </div>
                </div>
            </ul>
        </div>

        <dialog id="projectModal" class="modal">
            <div class="modal-box w-11/12 max-w-2xl">
                <h3 class="text-2xl font-bold mb-4">{{ selectedProject?.title }}</h3>
                <div class="relative w-full h-80 overflow-hidden">
                    <div v-for="(image, index) in selectedProject?.images" :key="index" class="absolute w-full h-full top-0 left-0 transition-opacity duration-500" :class="{ 'opacity-100': index === currentImageIndex, 'opacity-0': index !== currentImageIndex }">
                        <img :src="image" class="w-full h-full object-contain rounded-lg" />
                    </div>
                    <button class="absolute top-1/2 left-2 transform -translate-y-1/2 bg-black p-2 rounded-full" @click.stop="prevImage">❮</button>
                    <button class="absolute top-1/2 right-2 transform -translate-y-1/2 bg-black p-2 rounded-full" @click.stop="nextImage">❯</button>
                </div>
                <p class="mt-6 text-lg leading-relaxed">{{ selectedProject?.description }}</p>
                <div class="modal-action">
                    <form method="dialog">
                        <button class="btn">Close</button>
                    </form>
                </div>
            </div>
        </dialog>
    </section>
</template>

<script setup>
import { ref, computed } from 'vue';

import dashboard1 from "@/assets/projects/Dashboards/project-1.jpeg";
import dashboard2 from "@/assets/projects/Dashboards/project-2.jpeg";
import dashboard3 from "@/assets/projects/Dashboards/project-3.jpeg";

import ais1 from "@/assets/projects/AIS/project-1.jpeg";
import ais2 from "@/assets/projects/AIS/project-2.jpeg";
import ais3 from "@/assets/projects/AIS/project-3.jpeg";

import dss1 from "@/assets/projects/DSS/project-1.jpeg";
import dss2 from "@/assets/projects/DSS/project-2.jpeg";
import dss3 from "@/assets/projects/DSS/project-3.jpeg";

import dsr1 from "@/assets/projects/DSR/project-1.jpeg";
import dsr2 from "@/assets/projects/DSR/project-2.jpeg";
import dsr3 from "@/assets/projects/DSR/project-3.jpeg";
import dsr4 from "@/assets/projects/DSR/project-4.jpeg";
import dsr5 from "@/assets/projects/DSR/project-5.jpeg";

import gis1 from "@/assets/projects/GIS/project-1.jpeg";
import gis2 from "@/assets/projects/GIS/project-2.jpeg";
import gis3 from "@/assets/projects/GIS/project-3.jpeg";
import gis4 from "@/assets/projects/GIS/project-4.jpeg";

import dls1 from "@/assets/projects/DLS/project-1.jpeg";
import dls2 from "@/assets/projects/DLS/project-2.jpeg";
import dls3 from "@/assets/projects/DLS/project-3.jpeg";
import dls4 from "@/assets/projects/DLS/project-4.jpeg";

const Projects = ref([
    {
        id: 1,
        category: 'Web Development',
        images: [dls1, dls2, dls3, dls4],
        title: 'Document Library System',
        description: 'A secure document management platform built with Laravel 12, React, and ShadCN UI. Designed for organizations that need a centralized and confidential space to upload, manage, and share documents, DLS features role-based access control and LDAP authentication for seamless integration with enterprise directories. It balances flexibility, security, and usability for efficient document workflows.',
        technologies: ['Laravel', 'React JS', 'Inertia', 'PHP', 'ShadCN UI'],
    },
    {
        id: 2,
        category: 'Web Development',
        images: [dashboard1, dashboard2, dashboard3],
        title: 'Agriculture Dashboards',
        description: 'A comprehensive web-based dashboard system designed to visualize key performance indicators (KPIs), insights, and critical operational data for the banana industry. The dashboards cater to different parameters and operations, enabling management to make data-driven decisions that enhance productivity and efficiency. Using Vue.js for the frontend and PHP for the backend, this project offers interactive charts, real-time data updates, and customizable reports to provide a clear overview of farm performance, supply chain metrics, and other essential indicators.',
        technologies: ['Vue JS', 'PHP'],
    },
    {
        id: 3,
        category: 'Web Development',
        images: [ais1, ais2, ais3],
        title: 'Agriculture Information System',
        description: 'A collaborative web application designed to generate insightful reports, visualizations, and analyses for different departments within the agricultural sector. This system consolidates raw data and transforms it into structured dashboards, graphs, and tables, helping teams analyze trends, identify key patterns, and improve operational strategies. Built with JavaScript and PHP, the system ensures seamless data representation, enabling stakeholders to make well-informed decisions.',
        technologies: ['Javascript', 'PHP'],
    },
    {
        id: 4,
        category: 'Web Development',
        images: [dss1, dss2, dss3],
        title: 'Data Submission System',
        description: 'A web-based system designed to streamline the data submission process for field staff. Instead of direct data entry, field staff manually encode their data in Excel, where a VBA script checks for errors and ensures data accuracy before generating a CSV file. This CSV is then uploaded through the web app, which stores the data in a structured database. I was responsible for developing the backend logic to validate and process uploaded files, ensuring that only clean and verified data is accepted. The system also includes an admin panel for managing users, parameters, and access levels, making it easier to generate accurate reports and insights.',
        technologies: ['Javascript', 'PHP'],
    },
    {
        id: 5,
        category: 'Web Development',
        images: [dsr1, dsr2, dsr3, dsr4, dsr5],
        title: 'Data & Service Request System',
        description: 'A web-based request management system that enables employees from different departments to request specific datasets, whether raw, processed, or cleaned, for use in their reports and analyses. Additionally, the system allows users to request services such as custom dashboard development, data visualization, and web application solutions tailored to their needs. Built using JavaScript and PHP, this platform streamlines internal data-sharing processes, making it easier for teams to collaborate and leverage data for better decision-making.',
        technologies: ['Javascript', 'PHP'],
    },
    {
        id: 6,
        category: 'Web Development',
        images: [gis1, gis2, gis3, gis4],
        title: 'Geographical Information System',
        description: 'A GIS-based system developed to map and monitor banana plantations efficiently. The project started with manually drawing plantation boundaries using Inkscape, where the shapes were color-coded based on various plantation data and legend classifications. Over time, the system transitioned to Google Maps API, allowing satellite imagery layers to be overlaid with real-time plantation data. Additionally, drone-captured images are integrated as a separate layer, providing quarterly insights into plantation conditions. QGIS was also utilized to ensure accurate shape drawing and geospatial analysis, making the system a powerful tool for farm monitoring and decision-making.',
        technologies: ['Javascript', 'Vue JS', 'PHP', 'Inkscape', 'QGIS'],
    },
]);

const selectedCategory = ref('All');
const filteredProjects = computed(() => {
    if (selectedCategory.value === 'All') return Projects.value;
    return Projects.value.filter(project => project.category.toLowerCase() === selectedCategory.value.toLowerCase());
});

const selectedProject = ref(null);
const currentImageIndex = ref(0);

const openModal = (project) => {
    selectedProject.value = project;
    currentImageIndex.value = 0;
    document.getElementById('projectModal').showModal();
};

const closeModal = () => {
    document.getElementById('projectModal').close();
    selectedProject.value = null;
};

const nextImage = () => {
    if (selectedProject.value) {
        currentImageIndex.value = (currentImageIndex.value + 1) % selectedProject.value.images.length;
    }
};

const prevImage = () => {
    if (selectedProject.value) {
        currentImageIndex.value = (currentImageIndex.value - 1 + selectedProject.value.images.length) % selectedProject.value.images.length;
    }
};

const truncateDescription = (desc) => {
    const words = desc.split(' ');
    return words.length > 20 ? words.slice(0, 20).join(' ') + '...' : desc;
};
</script>

<style scoped></style>