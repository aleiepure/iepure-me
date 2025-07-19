<script setup>
import { ref, onMounted } from 'vue';
import ProjectCard from './ProjectCard.vue';

const universityProjects = ref([
    {
        icon: '../assets/images/projects/walkaware.png',
        title: 'WalkAware Trento',
        subtitle: 'University project',
        description: 'Awarded first prize by the Comune di Trento and Banca per il Trentino-Alto Adige, this app turns walking into rewards while supporting local businesses. Users earn points, discover events, report municipal issues, and contribute to a thriving local economy.',
        links: [
            {
                type: 'article',
                url: 'https://mag.unitn.it/innovazione/121316/100-progetti-per-il-comune-di-trento',
                icon: 'fa-newspaper',
                stats: null
            },
            {
                type: 'article',
                url: 'https://www.palazzobenvenuti.it/it-IT/-/blog/100-progetti-per-il-comune-di-trento',
                icon: 'fa-newspaper',
                stats: null
            }
        ]
    }
]);

const fossProjects = ref([
    {
        icon: '../assets/images/projects/devtoolbox.png',
        title: 'Dev Toolbox',
        subtitle: 'Development tools at your fingertips',
        description: 'Tired of endlessly looking online for the right tool, or to find again that website of which you don\'t recall the name to do a quick conversion? This is the right app for you.',
        links: [
            {
                type: 'github',
                url: 'https://github.com/aleiepure/devtoolbox',
                icon: 'fa-github',
                stats: '300+'
            },
            {
                type: 'download',
                url: 'https://flathub.org/apps/details/me.iepure.devtoolbox',
                icon: 'fa-download',
                stats: '50k+'
            }
        ]
    },
    {
        icon: '../assets/images/projects/ticketbooth.png',
        title: 'Ticket Booth',
        subtitle: 'Keep track of your favorite shows',
        description: 'Build your watch list of movies and TV Shows, keep track of watched titles, and find information about the latest releases with a beautiful GTK interface.',
        links: [
            {
                type: 'github',
                url: 'https://github.com/aleiepure/ticketbooth',
                icon: 'fa-github',
                stats: '80+'
            },
            {
                type: 'download',
                url: 'https://flathub.org/apps/details/me.iepure.Ticketbooth',
                icon: 'fa-download',
                stats: '10k+'
            }
        ]
    }
]);
</script>

<template>
    <section class="pt-24 pb-8 bg-cover" style="background-image: url('/background.jpg');">
        <div class="max-w-6xl mx-auto px-4">
            <!-- Section Header -->
            <div class="text-left mb-10">
                <h1 class="text-4xl lg:text-5xl font-bold text-white mb-4">My Projects</h1>
                <p class="text-lg text-gray-300">
                    Here you can find projects that I have worked on. Look at my GitHub profile for an
                    always up-to-date list.
                </p>
            </div>

            <!-- University Projects Section -->
            <div class="mb-12">
                <h3 class="text-2xl lg:text-3xl font-bold text-white mb-8 text-left">University Projects</h3>
                <div class="space-y-8">
                    <ProjectCard v-for="project in universityProjects" :key="project.title" :project="project" />
                </div>
            </div>

            <!-- FOSS Apps Section -->
            <div class="mb-8">
                <h3 class="text-2xl lg:text-3xl font-bold text-white mb-8 text-left">FOSS Apps</h3>
                <div class="space-y-8">
                    <ProjectCard v-for="project in fossProjects" :key="project.title" :project="project" />
                </div>
            </div>

        </div>
    </section>
</template>
