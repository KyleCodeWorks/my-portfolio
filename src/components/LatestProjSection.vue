<template>
    <section class="mt-20" id="projects">
        <div class="px-4 xl:pl-16">
            <div class="mb-4 md:flex md:justify-between xl:pr-16">
                <h2 class="text-4xl font-bold"> My Latest Projects</h2>
                <div class="flex space-x-4 mb-4 mt-5 md:mt-0">
                    <button class="hover:text-primary" v-for="category in ['all', 'web development', 'Mobile App']"
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
                            <span class="text-white text-2xl">🔍</span>
                        </button>
                    </div>
                    <div class="rounded-b-xl mt-3 bg-base-100 shadow-lg py-6 px-4">
                        <h3 class="text-lg font-semibold uppercase lg:text-xl"> {{ project.title }}</h3>
                        <p class="text-[#ADB7BE]">{{ truncateDescription(project.description) }} <span v-if="project.description.split(' ').length > 20" class="text-primary cursor-pointer" @click="openModal(project)">(read more)</span></p>
                        <div class="flex flex-wrap p-2.5">
                            <div v-for="technology in project.technologies" :key="technology"
                                class="text-center ml-1 mt-1 rounded-3xl bg-[#111827] border border-[#111827] backdrop-blur-md">
                                <span class="px-1 py-2 badge badge-md badge-info">{{ technology }}</span>
                            </div>
                        </div>
                    </div>
                </div>
            </ul>
        </div>

        <dialog id="projectModal" class="modal">
            <div class="modal-box w-11/12 max-w-5xl">
                <h3 class="text-2xl font-bold mb-4">{{ selectedProject?.title }}</h3>
                <div class="relative w-full h-80 overflow-hidden">
                    <div v-for="(image, index) in selectedProject?.images" :key="index" class="absolute w-full h-full top-0 left-0 transition-opacity duration-500" :class="{ 'opacity-100': index === currentImageIndex, 'opacity-0': index !== currentImageIndex }">
                        <img :src="image" class="w-full h-full object-cover rounded-lg" />
                    </div>
                    <button class="absolute top-1/2 left-2 transform -translate-y-1/2 bg-black text-white p-2 rounded-full" @click.stop="prevImage">❮</button>
                    <button class="absolute top-1/2 right-2 transform -translate-y-1/2 bg-black text-white p-2 rounded-full" @click.stop="nextImage">❯</button>
                </div>
                <p class="mt-6 text-gray-700 text-lg leading-relaxed">{{ selectedProject?.description }}</p>
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

const Projects = ref([
    {
        id: 1,
        category: 'web development',
        images: [
            "src/assets/projects/project-1/project-1.jpeg",
            "src/assets/projects/project-1/project-2.jpeg",
            "src/assets/projects/project-1/project-3.jpeg",
        ],
        title: 'Project 1',
        description: 'A web development project using Vue.js.',
        technologies: ['Vue.js 3', 'Vuex', 'Express'],
    },
    {
        id: 2,
        category: 'Mobile App',
        images: ['src/assets/mobile.jpg'],
        title: 'Mobile App Project',
        description: 'A mobile app built with modern technologies.',
        technologies: ['Vue.js 3', 'Capacitor', 'Firebase'],
    }
]);

const selectedCategory = ref('all');
const filteredProjects = computed(() => {
    if (selectedCategory.value === 'all') return Projects.value;
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