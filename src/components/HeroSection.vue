<template>
    <div class="hero min-h-screen relative">
        <div class="hero-content flex-col md:flex-row" data-aos="zoom-in-up">
            <div class="relative">
                <!-- Lightning Effect -->
                <div
                    class="absolute inset-0 w-full h-full bg-gradient-to-tr opacity-50 from-[#570cac] to-primary blur-2xl rounded-lg">
                </div>
                <!-- Image -->
                <img src="@/assets/top_picture.png" class="relative z-10 md:max-w-sm rounded-lg shadow-2xl" />
            </div>
            <div class="md:ml-10 lg:ml-20">
                <h1 class="text-5xl font-bold md:text-left text-center">Hey, I'm Kyle!</h1>
                <p class="text-xl py-6">
                    Experienced data analyst with over 6 years of expertise in SQL, database management, and advanced data
                    visualization techniques. Proficient in transforming complex datasets into actionable insights
                    through data modeling, trend analysis, and predictive analytics. Skilled in web development using
                    PHP to create dynamic applications that streamline processes and enhance operational efficiency.
                    Dedicated to leveraging analytics and web technologies to drive informed decision-making, optimize
                    workflows, and deliver measurable improvements in business outcomes.
                </p>
                <div class="flex items-center gap-x-4">
                    <a href="#about" class="btn btn-primary">
                        More About Me
                    </a>
                    <a href="/my-portfolio/Resume.pdf" download="KyleSoriben_Resume.pdf"
                        class="btn btn-primary hover:scale-105 transition-all ease-in-out">
                        Download Resume
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import AOS from 'aos';
import 'aos/dist/aos.css';
AOS.init();
</script>