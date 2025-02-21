<template>
    <section class="mt-20" id="about">
        <div class="md:grid md:grid-cols-2 gap-8 items-center py-8 px-4 xl:gap-16 xl:px-16">
            <!-- Education Section -->
            <div data-aos="flip-left">
                <h2 class="text-4xl font-bold text-left mb-8 md:mt-0 mt-8">My
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">Education</span>
                </h2>
                <div class="space-y-8 py-8" data-aos="fade-left">
                    <div class="grid grid-cols-1 gap-4">
                        <div v-for="element in education" :key="element.id"
                            class="grid grid-cols-4 items-center card bg-base-100 rounded-box p-4">
                            <!-- Left: Image taking 1/3 of the space -->
                            <div class="flex justify-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    stroke-width="1.5" stroke="currentColor" class="w-20 h-20 object-contain">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M4.26 10.147a60.438 60.438 0 0 0-.491 6.347A48.62 48.62 0 0 1 12 20.904a48.62 48.62 0 0 1 8.232-4.41 60.46 60.46 0 0 0-.491-6.347m-15.482 0a50.636 50.636 0 0 0-2.658-.813A59.906 59.906 0 0 1 12 3.493a59.903 59.903 0 0 1 10.399 5.84c-.896.248-1.783.52-2.658.814m-15.482 0A50.717 50.717 0 0 1 12 13.489a50.702 50.702 0 0 1 7.74-3.342M6.75 15a.75.75 0 1 0 0-1.5.75.75 0 0 0 0 1.5Zm0 0v-3.675A55.378 55.378 0 0 1 12 8.443m-7.007 11.55A5.981 5.981 0 0 0 6.75 15.75v-1.5" />
                                </svg>
                            </div>
                            <!-- Right: Details taking 2/3 of the space -->
                            <div class="col-span-3 pl-4 text-left">
                                <h3
                                    class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">
                                    {{ element.School }}
                                </h3>
                                <p>{{ element.program }}</p>
                                <p>{{ element.year }}</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- More About Me Section -->
            <div class="mt-4 md:mt-0 text-left flex flex-col h-full" data-aos="flip-right">
                <h2 class="text-4xl font-bold text-center mb-4">More
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">About
                        Me</span>
                </h2>
                <div class="text-center lg:text-left mt-8 py-8 space-y-6">
                    <p class="lg:text-lg">
                        I’m passionate about solving problems through technology and creating better solutions. I enjoy
                        learning new tools and methods to make my code clean, organized, and readable. Collaboration and
                        sharing newly acquired knowledge are integral parts of my work ethic.
                    </p>
                    <p class="lg:text-lg">
                        Outside of work, I value a balanced lifestyle. My hobbies include exploring food, biking,
                        playing
                        video games, and enjoying music—whether it's playing the guitar, singing, or just listening.
                    </p>
                    <p class="lg:text-lg">
                        I also participate in activities such as donating blood to help people in need.
                    </p>
                    <p class="lg:text-lg">
                        I'm always eager to embrace new challenges and continuously grow, both personally and
                        professionally.
                    </p>
                </div>


                <!-- KPI Boxes Section -->
                <div class="stats stats-vertical lg:stats-horizontal shadow">
                    <div class="stat place-items-center">
                        <div class="stat-figure text-secondary">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                class="inline-block h-8 w-8 stroke-current">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                    d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                            </svg>
                        </div>
                        <div class="stat-title">Years of Experience</div>
                        <div class="stat-value text-yellow-400">+6</div>
                    </div>

                    <div class="stat place-items-center">
                        <div class="stat-figure text-secondary">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                class="inline-block h-8 w-8 stroke-current">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                    d="M13 10V3L4 14h7v7l9-11h-7z"></path>
                            </svg>
                        </div>
                        <div class="stat-title">Status</div>
                        <div class="stat-value text-green-400">200</div>
                    </div>

                    <div class="stat place-items-center">
                        <div class="stat-figure text-secondary">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                class="inline-block h-8 w-8 stroke-current">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                    d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z">
                                </path>
                            </svg>
                        </div>
                        <div class="stat-title">Blood Donations</div>
                        <div class="stat-value text-red-400">+12</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

</template>
<script setup>
import { ref } from 'vue';
const education = ref([
    {
        id: 1,
        School: 'UNIVERSITY OF SOUTHEASTHERN PHILIPPINES',
        program: 'BS in Information Technology',
        year: '2018'
    }
])
</script>
