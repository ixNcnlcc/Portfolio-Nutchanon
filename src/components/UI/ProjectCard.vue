<script setup>
defineProps({
    title: {
        type: String,
        required: true,
        default: 'Project Title'
    },
    description: {
        type: String,
        required: true,
        default: 'Project Description'
    },  
    image: {
        type: String,
        required: true,
        default: '/'
    },
    tags: {
        type: Array,
        required: false,
        default: () => ['Vue.js', 'Tailwind css', 'JavaScript']
    },
    liveLink: {
        type: String,
        required: false,
        default: null
    },
    codeLink: {
        type: String,
        required: false,
        default: null
    }
})
</script>

<template>
    <article class="max-x-sm overflow-hidden shadow-lg rounded border border-secondary dark:border-[#ffffff29]
    bg-primary">
        <figure class="relative overflow-hidden">
            <img :src="image" :alt="title" class="w-full h-48 object-cover transition-transform duration-300 hover:scale-105">
            <div class="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300"></div>
        </figure>
        
        <section class="px-6 py-4">
            <header>
                <h3 class="font-bold text-xl mn-2 text-white">{{ title }}</h3>
            </header>
            <p class="text-gray-300 text-sm">{{ description }}</p>
        </section>
        
        <footer class="px-6 pt-4 pb-2">
            <ul class="flex flex-wrap gap-2">
                <li v-for="(tag,index) in tags" :key="index" 
                class="inline-block dark:bg-primary bg-gray-700 text-gray-200 rounded-full px-3 py-1
                text-sm font-semibold">
                   # {{ tag }}
                </li>
            </ul>
        </footer>

        <div class="px-6 pb-4 flex justify-between items-center">
            <a :href="liveLink" v-if="liveLink" class="text-secondary font-semibold hover:underline text-sm">Live Demo</a>
            <a :href="codeLink" v-if="codeLink" class="text-secondary font-semibold hover:underline text-sm">View Code</a>
        </div>
    </article>
</template>