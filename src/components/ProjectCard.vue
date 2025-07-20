<script setup>
import { computed } from 'vue';

const props = defineProps({
    project: {
        type: Object,
        required: true
    }
});
</script>

<template>
    <div
        class="project-card bg-white rounded-lg overflow-hidden transition-all duration-300 hover:-translate-y-2 hover:shadow-xl">
        <div class="flex flex-col lg:flex-row items-start p-6 lg:p-8">

            <!-- Project Icon -->
            <div class="flex-shrink-0 mb-4 lg:mb-0 lg:mr-6">
                <img :src="project.icon" :alt="project.title"
                    class="w-16 h-16 lg:w-24 lg:h-24 object-contain rounded-lg">
            </div>

            <!-- Project Info -->
            <div class="flex-grow">
                <h4 class="text-xl lg:text-2xl font-bold text-gray-900 mb-2">
                    {{ project.title }}
                </h4>
                <h5 class="text-base lg:text-lg text-blue-600 font-medium mb-3">
                    {{ project.subtitle }}
                </h5>
                <p class="text-gray-700 mb-4 leading-relaxed">
                    {{ project.description }}
                </p>

                <!-- Project Links -->
                <div class="flex flex-wrap gap-4">
                    <a v-for="(link, index) in project.links" :key="index" :href="link.url" target="_blank"
                        rel="noopener noreferrer"
                        class="inline-flex items-center px-4 py-2 bg-gray-100 hover:bg-blue-500 hover:text-white text-gray-700 rounded-lg transition-colors duration-200">
                        <i :class="`fa ${link.icon} mr-2`"></i>
                        <span class="text-sm font-medium">
                            <template v-if="link.type === 'github'">
                                GitHub
                                <span v-if="link.stats" class="ml-1 text-xs opacity-75">
                                    (★{{ link.stats }})
                                </span>
                            </template>
                            <template v-else-if="link.type === 'download'">
                                Download
                                <span v-if="link.stats" class="ml-1 text-xs opacity-75">
                                    ({{ link.stats }})
                                </span>
                            </template>
                            <template v-else-if="link.type === 'article'">
                                Article
                            </template>
                        </span>
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.project-card {
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
}

.project-card:hover {
    box-shadow: 0 25px 50px -12px rgba(255, 255, 255, 0.25);
}
</style>