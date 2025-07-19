<script setup lang="ts">
import { ref } from 'vue'

const currentYear = ref(new Date().getFullYear())
</script>

<template>
    <footer class="text-white py-4 mt-auto w-full" :style="{ backgroundColor: '#272727' }">
        <div class="container mx-auto text-center">
            <p>&copy; {{ currentYear }} Alessandro Iepure</p>
        </div>
    </footer>
</template>