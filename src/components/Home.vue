<script setup>
import avatarUrl from '../assets/images/avatar.png';
</script>

<template>
    <section class="pt-24 pb-8 min-h-screen flex items-center bg-cover"
        style="background-image: url('/background.jpg');">
        <div class="mx-auto px-4 py-12">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 lg:gap-12 items-center min-h-full">

                <!-- Left Content -->
                <div class="flex flex-col justify-center text-center lg:text-center order-2 lg:order-1">
                    <h1 class="text-3xl lg:text-6xl font-bold text-white mb-6">
                        Hello stranger 👋!<br />I'm Alessandro
                    </h1>
                    <h2 class="text-xl lg:text-3xl text-gray-300 mb-8">
                        CS Student | Developer | Tech Enthusiast
                    </h2>
                    <div class="flex justify-center lg:justify-center space-x-8">
                        <a href="mailto:alessandro@iepure.me?subject=[Website]&body=Hi!%20I%20have%20a%20question"
                            target="_blank" rel="noopener noreferrer"
                            class="text-white text-3xl hover:text-blue-500 transition-colors duration-200">
                            <i class="fa fa-envelope"></i>
                        </a>
                        <a href="https://github.com/aleiepure" target="_blank" rel="noopener noreferrer"
                            class="text-white text-3xl hover:text-blue-500 transition-colors duration-200">
                            <i class="fa fa-github"></i>
                        </a>
                        <a href="https://www.linkedin.com/in/alessandroiepure/" target="_blank"
                            rel="noopener noreferrer" class="text-white text-3xl hover:text-blue-500 transition-colors duration-200">
                            <i class="fa fa-linkedin"></i>
                        </a>
                    </div>
                </div>

                <!-- Right Avatar -->
                <div class="flex justify-center lg:justify-center order-1 lg:order-2">
                    <img :src="avatarUrl" alt="Avatar" id="avatar" class="w-72 h-72 lg:w-96 lg:h-96 object-cover">
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
#avatar {
    animation: up-down 3s ease-in-out infinite alternate-reverse both;
}

@keyframes up-down {
    0% {
        transform: translateY(10px);
    }

    100% {
        transform: translateY(-10px);
    }
}
</style>