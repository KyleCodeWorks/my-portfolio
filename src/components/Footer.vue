<script setup>
import { ref, onMounted } from "vue";

// Get current year
const currentYear = new Date().getFullYear();
const visitCount = ref(0);

// Load environment variables
const binId = import.meta.env.VITE_JSONBIN_ID; // Correct way to access Vite .env variables
const apiKey = import.meta.env.VITE_JSONBIN_API_KEY; // Correct way to access Vite .env variables


const fetchVisitorCount = async () => {
    try {
    const response = await fetch(`https://api.jsonbin.io/v3/b/${binId}/latest`, {
        method: "GET",
        headers: {
        "X-Master-Key": apiKey,
        "Content-Type": "application/json",
        },
    });

    if (!response.ok) {
        throw new Error(`HTTP error! Status: ${response.status}`);
    }

    const data = await response.json();
    visitCount.value = data.record?.visitCount || 0;
    } catch (error) {
    console.error("Error fetching visit count:", error);
    visitCount.value = 0; // Set default value to avoid UI breakage
    }

};

const updateVisitorCount = async () => {
    try {
    visitCount.value += 1;

    const response = await fetch(`https://api.jsonbin.io/v3/b/${binId}`, {
        method: "PUT",
        headers: {
        "X-Master-Key": apiKey,
        "Content-Type": "application/json",
        },
        body: JSON.stringify({ visitCount: visitCount.value }),
    });

    if (!response.ok) {
        throw new Error(`HTTP error! Status: ${response.status}`);
    }
    } catch (error) {
    console.error("Error updating visit count:", error);
    }

};

// Fetch and update visit count on component mount
onMounted(async () => {
  await fetchVisitorCount();
  await updateVisitorCount();
});
</script>
<template >
    <footer class="mt-8 border z-10 border-t-[#33353F] border-l-transparent border-r-transparent">
        <div class="container p-12 flex">
            <p>All rights reserved.</p>
        </div>
    </footer>
</template>
