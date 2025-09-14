<script setup>
import { defineProps } from "vue";

// Component props
defineProps({
  label: {
    type: String,
    default: "Button",
  },
  onClick: {
    type: Function,
    default: () => {},
  },
});
</script>

<template>
  <button
    @click="onClick"
    class="group relative overflow-hidden rounded-2xl bg-slate-900 dark:bg-slate-800 text-white font-bold px-8 py-4 text-lg flex justify-center items-center transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-blue-500/25 border-2 border-slate-700 dark:border-slate-600 hover:border-blue-500"
  >
    <!-- Animated background pattern -->
    <div
      class="absolute inset-0 bg-gradient-to-br from-blue-500/0 via-purple-500/0 to-pink-500/0 group-hover:from-blue-500/10 group-hover:via-purple-500/10 group-hover:to-pink-500/10 transition-all duration-500"
    />

    <!-- Content -->
    <div class="relative flex items-center space-x-3 z-10">
      <div class="relative">
        <Icon
          icon="mdi:email-outline"
          class="text-2xl group-hover:animate-bounce"
        />
        <div
          class="absolute -top-1 -right-1 w-3 h-3 bg-red-500 rounded-full group-hover:animate-ping"
        />
      </div>
      <span class="group-hover:text-blue-400 transition-colors duration-300">
        {{ label }}
      </span>
    </div>

    <!-- Corner accents -->
    <div
      class="absolute top-0 left-0 w-4 h-4 border-t-2 border-l-2 border-blue-500 opacity-0 group-hover:opacity-100 transition-opacity duration-300"
    />
    <div
      class="absolute bottom-0 right-0 w-4 h-4 border-b-2 border-r-2 border-blue-500 opacity-0 group-hover:opacity-100 transition-opacity duration-300"
    />

    <!-- Floating particles -->
    <div
      class="absolute top-2 left-4 w-1 h-1 bg-blue-400 rounded-full opacity-0 group-hover:opacity-100 group-hover:animate-ping"
      style="animation-delay: 0.1s"
    />
    <div
      class="absolute top-4 right-6 w-1 h-1 bg-purple-400 rounded-full opacity-0 group-hover:opacity-100 group-hover:animate-ping"
      style="animation-delay: 0.3s"
    />
    <div
      class="absolute bottom-3 left-6 w-1 h-1 bg-pink-400 rounded-full opacity-0 group-hover:opacity-100 group-hover:animate-ping"
      style="animation-delay: 0.5s"
    />
  </button>
</template>

<style scoped>
/* Custom animations for button effects */
.group:hover .group-hover\:scale-105 {
  transform: scale(1.05);
}

/* Smooth transitions for all elements */
* {
  transition-property: color, background-color, border-color,
    text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter,
    backdrop-filter;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}
</style>
