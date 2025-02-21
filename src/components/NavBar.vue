<template>
    <div class="navbar bg-base-100/90 shadow-sm">
        <div class="navbar-start">
            <div class="dropdown">
                <div tabindex="0" role="button" class="btn btn-ghost lg:hidden">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24"
                        stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M4 6h16M4 12h8m-8 6h16" />
                    </svg>
                </div>
                <ul tabindex="0" class="menu bg-base-100 menu-sm dropdown-content rounded-box z-1 mt-3 w-52 p-2 shadow">
                    <li v-for="item in Menu" :key="item.name">
                        <a :href="item.href" class="block transition ease-linear"
                            @click="scrollToSection(item.href)">
                            {{ item.name }}
                        </a>
                    </li>
                </ul>
            </div>
            <a href="#about" class="btn btn-ghost text-xl">KYLE SORIBEN</a>
        </div>

        <div class="navbar-end hidden lg:flex">
            <ul class="menu menu-horizontal px-1">
                <li v-for="item in Menu" :key="item.name">
                    <a :href="item.href" class="block transition ease-linear"
                        @click="scrollToSection(item.href)">
                        {{ item.name }}
                    </a>
                </li>
            </ul>
        </div>
    </div>

</template>
<script setup>
import { ref } from 'vue';
const Menu = ref([
    { name: 'Services', href: '#services' },
    { name: 'About Me', href: '#about' },
    { name: 'Skills', href: '#skills' },
    { name: 'Projects', href: '#projects' },
    { name: 'Contact', href: '#contact' },
]);

const isMenuOpen = ref(false)
const scrollToSection = (href) => {
    isMenuOpen.value = false;
    const section = document.querySelector(href);
    if (section) {
        section.scrollIntoView({ behavior: 'smooth' });
    }

}

</script>