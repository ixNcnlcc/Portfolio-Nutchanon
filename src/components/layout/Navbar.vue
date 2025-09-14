<script setup>
import { ref, onMounted, onUnmounted } from "vue";

// State
const isMenuOpen = ref(false);
const isScrolled = ref(false);
const isDarkMode = ref(localStorage.getItem("theme") === "dark");

// Constants
const NAVBAR_OFFSET = 0;
const SCROLL_THRESHOLD = 50;
const SCROLL_DELAY = 10;

// Menu configuration
const menuItems = ref([
  { name: "Home", href: "#top", icon: "mdi:home" },
  { name: "Services", href: "#services", icon: "mdi:briefcase" },
  { name: "Skills", href: "#skills", icon: "mdi:code-tags" },
  { name: "Why Me", href: "#why-me", icon: "mdi:account-star" },
  { name: "Projects", href: "#projects", icon: "mdi:folder-multiple" },
  { name: "Contact", href: "#contact", icon: "mdi:email" },
]);

// Navigation functions
const scrollToSection = (href) => {
  isMenuOpen.value = false;

  if (href === "#top") {
    window.scrollTo({ top: 0, behavior: "smooth" });
    return;
  }

  const section = document.querySelector(href);
  if (!section) return;

  const navbar = document.querySelector("header");
  const navbarHeight = navbar?.offsetHeight || 80;
  const sectionTop = section.offsetTop - navbarHeight - NAVBAR_OFFSET;

  setTimeout(() => {
    window.scrollTo({
      top: Math.max(0, sectionTop),
      behavior: "smooth",
    });
  }, SCROLL_DELAY);
};

// Theme functions
const toggleDarkMode = () => {
  const html = document.documentElement;
  const newTheme = isDarkMode.value ? "light" : "dark";

  html.classList.toggle("dark", newTheme === "dark");
  localStorage.setItem("theme", newTheme);
  isDarkMode.value = !isDarkMode.value;
};

// Menu functions
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

// Event handlers
const handleScroll = () => {
  isScrolled.value = window.scrollY > SCROLL_THRESHOLD;
};

const handleEscape = (e) => {
  if (e.key === "Escape") {
    isMenuOpen.value = false;
  }
};

// Lifecycle
onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  document.addEventListener("keydown", handleEscape);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
  document.removeEventListener("keydown", handleEscape);
});
</script>

<template>
  <header
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300 w-full max-w-full',
      isScrolled
        ? 'bg-white/90 dark:bg-slate-900/90 backdrop-blur-md shadow-lg'
        : 'bg-transparent',
    ]"
  >
    <nav class="container mx-auto px-4 py-4">
      <div class="flex items-center justify-between">
        <!-- Logo Section -->
        <div class="flex items-center space-x-2">
          <div
            class="w-10 h-10 bg-gradient-to-r from-blue-500 to-purple-600 rounded-lg flex items-center justify-center"
          >
            <Icon icon="mdi:code-braces" class="text-white text-xl" />
          </div>
          <span
            class="text-2xl font-bold bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent"
          >
            Nutchanon
          </span>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden lg:flex items-center space-x-8">
          <ul class="flex items-center space-x-6">
            <li v-for="item in menuItems" :key="item.name">
              <a
                :href="item.href"
                @click="scrollToSection(item.href)"
                class="group flex items-center space-x-2 px-3 py-2 rounded-lg text-slate-600 dark:text-slate-300 hover:text-blue-500 dark:hover:text-blue-400 hover:bg-blue-50 dark:hover:bg-blue-900/20 transition-all duration-300"
              >
                <Icon
                  :icon="item.icon"
                  class="text-lg group-hover:scale-110 transition-transform duration-300"
                />
                <span class="font-medium">{{ item.name }}</span>
              </a>
            </li>
          </ul>

          <!-- Theme Toggle -->
          <button
            @click="toggleDarkMode"
            class="p-3 rounded-lg bg-slate-100 dark:bg-slate-800 hover:bg-slate-200 dark:hover:bg-slate-700 transition-all duration-300 group"
          >
            <Icon
              :icon="isDarkMode ? 'mdi:weather-sunny' : 'mdi:weather-night'"
              class="text-xl text-slate-600 dark:text-slate-300 group-hover:scale-110 transition-transform duration-300"
            />
          </button>
        </div>

        <!-- Mobile Controls -->
        <div class="lg:hidden flex items-center space-x-4">
          <!-- Mobile Theme Toggle -->
          <button
            @click="toggleDarkMode"
            class="p-2 rounded-lg bg-slate-100 dark:bg-slate-800 hover:bg-slate-200 dark:hover:bg-slate-700 transition-all duration-300"
          >
            <Icon
              :icon="isDarkMode ? 'mdi:weather-sunny' : 'mdi:weather-night'"
              class="text-lg text-slate-600 dark:text-slate-300"
            />
          </button>

          <!-- Mobile Menu Toggle -->
          <button
            @click="toggleMenu"
            class="p-2 rounded-lg bg-slate-100 dark:bg-slate-800 hover:bg-slate-200 dark:hover:bg-slate-700 transition-all duration-300"
          >
            <Icon
              :icon="isMenuOpen ? 'mdi:close' : 'mdi:menu'"
              class="text-xl text-slate-600 dark:text-slate-300"
            />
          </button>
        </div>
      </div>

      <!-- Mobile Menu Dropdown -->
      <div
        :class="[
          'lg:hidden transition-all duration-300 ease-in-out',
          isMenuOpen
            ? 'max-h-96 opacity-100 mt-4'
            : 'max-h-0 opacity-0 overflow-hidden',
        ]"
      >
        <div
          class="bg-white dark:bg-slate-800 rounded-xl shadow-lg p-4 space-y-2"
        >
          <ul class="space-y-2">
            <li v-for="item in menuItems" :key="item.name">
              <a
                :href="item.href"
                @click="scrollToSection(item.href)"
                class="flex items-center space-x-3 px-4 py-3 rounded-lg text-slate-600 dark:text-slate-300 hover:text-blue-500 dark:hover:text-blue-400 hover:bg-blue-50 dark:hover:bg-blue-900/20 transition-all duration-300 group"
              >
                <Icon
                  :icon="item.icon"
                  class="text-lg group-hover:scale-110 transition-transform duration-300"
                />
                <span class="font-medium">{{ item.name }}</span>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<style scoped>
/* Hide scrollbar for mobile menu */
.overflow-hidden::-webkit-scrollbar {
  display: none;
}

/* Global transition settings */
* {
  transition-property: color, background-color, border-color,
    text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter,
    backdrop-filter;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}

/* Active navigation link styles */
.router-link-active {
  color: #3b82f6;
  background-color: #eff6ff;
}

.dark .router-link-active {
  color: #60a5fa;
  background-color: rgba(30, 58, 138, 0.2);
}

/* Hover scale animation */
.group:hover .group-hover\:scale-110 {
  transform: scale(1.1);
}

/* Backdrop blur support */
.backdrop-blur-md {
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
}
</style>
