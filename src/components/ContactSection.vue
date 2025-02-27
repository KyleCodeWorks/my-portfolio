<script setup>
import { ref } from "vue";
import emailjs from "emailjs-com";
import { useToast } from 'vue-toastification';

const toast = useToast();

// Reactive form data
const form = ref({
    email: "",
    name: "",
    message: "",
});

// Function to send email
const sendEmail = async () => {
    const templateParams = {
        from_name: form.value.name,
        from_email: form.value.email,
        message: form.value.message,
    };

    try {
        await emailjs.send(
            import.meta.env.VITE_EMAILJS_SERVICE_ID, // Service ID from .env
            import.meta.env.VITE_EMAILJS_TEMPLATE_ID, // Template ID from .env
            templateParams,
            import.meta.env.VITE_EMAILJS_PUBLIC_KEY // Public key from .env
        );

        // Reset the form
        form.value.email = "";
        form.value.name = "";
        form.value.message = "";

        toast.success("Thank you for contacting me, I'll get back to you soon.");
    } catch (error) {
        console.error("Failed to send email:", error);
        toast.error("Failed to send email.");
    }
};
</script>



<template>
    <section class="mt-20" id="contact">
        <div class="md:grid md:grid-cols-2 gap-8 items-center py-8 px-4 xl:gap-16 xl:px-16">
            <!-- Left Section -->
            <div data-aos="flip-left">
                <h2 class="text-4xl font-bold text-left mb-8 md:mt-0 mt-8">Let's
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary"> Connect
                        Together</span>
                </h2>
                <!-- Left Section -->
                <div class="flex flex-col items-center">
                    <!-- Intro Text -->
                    <p class="text-[#adb7be] mb-6 text-left">
                        Let’s work together to bring your ideas to life! Whether you have a new project in mind or need
                        help improving an existing one, I’m here to collaborate and provide the support you need. With a
                        focus on delivering quality results and meeting your goals, I’m excited to help you take the
                        next step. Don’t hesitate to reach out—let’s turn your vision into reality and create something
                        amazing together!
                    </p>

                    <!-- Stats Section -->
                    <div class="stats stats-vertical lg:stats-horizontal shadow mb-8">
                        <div class="stat place-items-center">
                            <div class="stat-figure text-secondary">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    class="inline-block h-8 w-8 stroke-current">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                                </svg>
                            </div>
                            <div class="stat-title">Email</div>
                            <div class="text-sm stat-value text-yellow-400">kylesoriben@gmail.com</div>
                        </div>

                        <div class="stat place-items-center">
                            <div class="stat-figure text-secondary">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    class="inline-block h-8 w-8 stroke-current">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M13 10V3L4 14h7v7l9-11h-7z"></path>
                                </svg>
                            </div>
                            <div class="stat-title">Address</div>
                            <div class="text-sm stat-value text-green-400">Panabo City, Davao del Norte</div>
                        </div>
                    </div>

                    <!-- Social Media Icons -->
                    <div class="flex justify-center space-x-8 mt-auto">
                        <a href="https://linkedin.com/in/your-profile" target="_blank"
                            class="text-blue-600 hover:text-blue-400">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 24 24"
                                class="w-8 h-8">
                                <path
                                    d="M19 0h-14c-2.762 0-5 2.238-5 5v14c0 2.762 2.238 5 5 5h14c2.762 0 5-2.238 5-5v-14c0-2.762-2.238-5-5-5zm-11.6 20h-2.4v-8h2.4v8zm-1.2-9.2c-.776 0-1.4-.624-1.4-1.4 0-.776.624-1.4 1.4-1.4.776 0 1.4.624 1.4 1.4 0 .776-.624 1.4-1.4 1.4zm11.2 9.2h-2.4v-4.8c0-1.128-.472-1.6-1.2-1.6-.744 0-1.2.472-1.2 1.6v4.8h-2.4v-8h2.4v.8c.608-.672 1.384-1.2 2.4-1.2 1.832 0 3.6 1.416 3.6 4v4.4zm0 0" />
                            </svg>
                        </a>
                        <a href="https://github.com/your-profile" target="_blank"
                            class="text-gray-400 hover:text-gray-200">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 24 24"
                                class="w-8 h-8">
                                <path
                                    d="M12 0c-6.627 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.387.6.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.757-1.333-1.757-1.089-.744.084-.729.084-.729 1.205.084 1.839 1.232 1.839 1.232 1.072 1.839 2.809 1.308 3.494.998.108-.777.42-1.308.763-1.611-2.665-.303-5.467-1.332-5.467-5.932 0-1.311.468-2.383 1.236-3.221-.123-.303-.537-1.522.117-3.176 0 0 1.008-.323 3.303 1.231.96-.268 1.992-.402 3.018-.408 1.026.006 2.058.14 3.018.408 2.295-1.554 3.303-1.231 3.303-1.231.654 1.654.24 2.873.117 3.176.768.838 1.236 1.91 1.236 3.221 0 4.61-2.807 5.625-5.478 5.922.432.372.816 1.104.816 2.226v3.293c0 .321.186.694.801.577 4.767-1.587 8.205-6.084 8.205-11.387 0-6.627-5.373-12-12-12z" />
                            </svg>
                        </a>
                    </div>
                </div>
            </div>

            <!-- Right Section -->
            <div class="mt-4 md:mt-0 text-left flex flex-col h-full" data-aos="flip-right">
                <h2 class="text-4xl font-bold text-center mb-4">Contact
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">Me</span>
                </h2>
                <div class="card card-sm overflow-hidden">
                    <div class="card-body gap-4">
                        <form @submit.prevent="sendEmail" class="space-y-4">
                            <!-- Email and Name Inputs -->
                            <div class="flex flex-col md:flex-row gap-4">
                                <!-- Email Input -->
                                <label class="input input-border flex items-center gap-2 grow">
                                    <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 16 16"
                                        class="h-5 w-5 opacity-70">
                                        <path
                                            d="M0 4a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2V4Zm2-.5a.5.5 0 0 0-.496.438l6.496 4.053 6.496-4.053A.5.5 0 0 0 14 3.5H2Zm12 1.923-5.804 3.625a.5.5 0 0 1-.392 0L2 5.423V12a1 1 0 0 0 1 1h10a1 1 0 0 0 1-1V5.423Z" />
                                    </svg>
                                    <input v-model="form.email" type="email" class="grow" placeholder="Email Address"
                                        required>
                                </label>
                                <!-- Name Input -->
                                <label class="input input-border flex items-center gap-2 grow">
                                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16" fill="currentColor"
                                        class="h-4 w-4 opacity-70">
                                        <path
                                            d="M8 8a3 3 0 1 0 0-6 3 3 0 0 0 0 6ZM12.735 14c.618 0 1.093-.561.872-1.139a6.002 6.002 0 0 0-11.215 0c-.22.578.254 1.139.872 1.139h9.47Z">
                                        </path>
                                    </svg>
                                    <input v-model="form.name" type="text" class="grow" placeholder="Name" required>
                                </label>
                            </div>
                            <!-- Message Input -->
                            <textarea v-model="form.message" placeholder="Message"
                                class="textarea h-64 w-full"></textarea>
                            <!-- Submit Button -->
                            <div class="card-actions items-center gap-6">
                                <button type="submit" class="btn btn-primary">Send Email</button>
                            </div>
                        </form>
                    </div>
                </div>
                <!-- Toast -->

            </div>

        </div>
    </section>

</template>
