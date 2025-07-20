<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isMobileMenuOpen = ref(false)
const isScrolled = ref(false)

const toggleMobileMenu = () => {
    isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const handleScroll = () => {
    isScrolled.value = window.scrollY > 0
}

onMounted(() => {
    window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
})

const navigation = [
    { name: 'Home', icon: 'fa-solid fa-house', href: '#/'},
    { name: 'Projects', icon: 'fa-solid fa-screwdriver-wrench', href: '#/projects'},
]
</script>

<template>
    <nav :class="[
        'fixed top-0 left-0 right-0 z-50 transition-all duration-150',
        isScrolled ? 'bg-gray-800' : 'bg-transparent'
    ]" :style="isScrolled || isMobileMenuOpen ? 'background-color: #272727;' : ''">
        <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
            <div class="relative flex h-16 items-center justify-between">

                <!-- Mobile menu button-->
                <div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
                    <button type="button" @click="toggleMobileMenu" aria-controls="mobile-menu" aria-expanded="false"
                        class="relative inline-flex items-center justify-center rounded-md p-2 text-gray-400 hover:bg-gray-700 hover:text-white focus:ring-2 focus:ring-white focus:outline-hidden focus:ring-inset">
                        <span class="absolute -inset-0.5"></span>
                        <span class="sr-only">Open main menu</span>

                        <!-- Icon when menu is closed -->
                        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" data-slot="icon"
                            aria-hidden="true" class="block size-6">
                            <path d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" stroke-linecap="round"
                                stroke-linejoin="round" />
                        </svg>

                        <!-- Icon when menu is open -->
                        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" data-slot="icon"
                            aria-hidden="true" class="hidden size-6">
                            <path d="M6 18 18 6M6 6l12 12" stroke-linecap="round" stroke-linejoin="round" />
                        </svg>
                    </button>
                </div>

                <!-- Left side -->
                <div class="flex flex-1 items-center justify-center sm:items-stretch sm:justify-start">
                    <div class="flex shrink-0 items-center">
                        <a :href="navigation[0].href" aria-current="page"
                            class="px-3 py-2 text-sm font-medium text-white uppercase">
                            Alessandro Iepure
                        </a>
                    </div>
                </div>
                <div class="absolute inset-y-0 right-0 flex items-center pr-2 sm:static sm:inset-auto sm:ml-6 sm:pr-0">
                    <div class="hidden sm:ml-6 sm:block">
                        <div class="flex space-x-4 relative">
                            <a v-for="item in navigation" :key="item.name" :href="item.href"
                                class="rounded-md px-3 py-2 text-sm font-medium text-gray-300 hover:bg-gray-700 hover:text-white">
                                <i :class="item.icon" class="mr-2"></i> {{ item.name }}
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Mobile menu, show/hide based on menu state. -->
        <div v-show="isMobileMenuOpen" id="mobile-menu" class="sm:hidden">
            <div class="space-y-1 px-2 pt-2 pb-3">
                <a v-for="item in navigation" :key="item.name" :href="item.href"
                    class="block rounded-md px-3 py-2 text-base font-medium text-gray-300 hover:bg-gray-700 hover:text-white">
                    <i :class="item.icon" class="mr-2"></i> {{ item.name }}
                </a>
            </div>
        </div>
    </nav>
</template>