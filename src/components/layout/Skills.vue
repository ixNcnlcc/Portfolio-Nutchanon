<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import CountUp from "vue-countup-v3";

// Constants
const OBSERVER_THRESHOLD = 0.3;

// Skills data with enhanced properties
const skills = ref([
  {
    id: 1,
    name: "HTML",
    percentage: 70,
    icon: "mdi:language-html5",
    color: "from-orange-500 to-red-500",
    bgColor: "from-orange-50 to-red-50 dark:from-orange-900/20 dark:to-red-900/20",
    borderColor: "border-orange-200 dark:border-orange-700",
    description: "โครงสร้างเว็บไซต์",
    level: "Expert"
  },
  {
    id: 2,
    name: "CSS",
    percentage: 60,
    icon: "mdi:language-css3",
    color: "from-blue-500 to-cyan-500",
    bgColor: "from-blue-50 to-cyan-50 dark:from-blue-900/20 dark:to-cyan-900/20",
    borderColor: "border-blue-200 dark:border-blue-700",
    description: "การออกแบบและจัดแต่ง",
    level: "Advanced"
  },
  {
    id: 3,
    name: "JavaScript",
    percentage: 60,
    icon: "mdi:language-javascript",
    color: "from-yellow-500 to-orange-500",
    bgColor: "from-yellow-50 to-orange-50 dark:from-yellow-900/20 dark:to-orange-900/20",
    borderColor: "border-yellow-200 dark:border-yellow-700",
    description: "การเขียนโปรแกรม",
    level: "Advanced"
  },
  {
    id: 4,
    name: "Vue.js",
    percentage: 50,
    icon: "mdi:vuejs",
    color: "from-green-500 to-emerald-500",
    bgColor: "from-green-50 to-emerald-50 dark:from-green-900/20 dark:to-emerald-900/20",
    borderColor: "border-green-200 dark:border-green-700",
    description: "Framework สำหรับ Frontend",
    level: "Intermediate"
  },
  {
    id: 5,
    name: "Tailwind CSS",
    percentage: 30,
    icon: "mdi:tailwind",
    color: "from-cyan-500 to-blue-500",
    bgColor: "from-cyan-50 to-blue-50 dark:from-cyan-900/20 dark:to-blue-900/20",
    borderColor: "border-cyan-200 dark:border-cyan-700",
    description: "CSS Framework",
    level: "Advanced"
  },
  {
    id: 6,
    name: "MySQL",
    percentage: 30,
    icon: "mdi:database",
    color: "from-purple-500 to-indigo-500",
    bgColor: "from-purple-50 to-indigo-50 dark:from-purple-900/20 dark:to-indigo-900/20",
    borderColor: "border-purple-200 dark:border-purple-700",
    description: "ฐานข้อมูล",
    level: "Intermediate"
  },
  {
    id: 7,
    name: "Figma",
    percentage: 40,
    icon: "mdi:figma",
    color: "from-pink-500 to-rose-500",
    bgColor: "from-pink-50 to-rose-50 dark:from-pink-900/20 dark:to-rose-900/20",
    borderColor: "border-pink-200 dark:border-pink-700",
    description: "การออกแบบ UI/UX",
    level: "Advanced"
  },
  {
    id: 8,
    name: "Git",
    percentage: 50,
    icon: "mdi:git",
    color: "from-gray-600 to-gray-800",
    bgColor: "from-gray-50 to-gray-100 dark:from-gray-800/20 dark:to-gray-900/20",
    borderColor: "border-gray-200 dark:border-gray-700",
    description: "Version Control",
    level: "Intermediate"
  }
]);

// Reactive state
const skillsSection = ref(null);
const hasIntersected = ref(false);
let observer = null;

// Intersection Observer setup
const setupObserver = () => {
  observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        hasIntersected.value = true;
        observer?.disconnect();
      }
    },
    { threshold: OBSERVER_THRESHOLD }
  );

  if (skillsSection.value) {
    observer.observe(skillsSection.value);
  }
};

// Lifecycle hooks
onMounted(() => {
  setupObserver();
});

onUnmounted(() => {
  observer?.disconnect();
});
</script>

<template>
  <section 
    ref="skillsSection"
    class="relative py-20 px-4 overflow-hidden"
    id="skills"
  >
    <!-- Background Elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div
        class="absolute -bottom-40 -right-40 w-80 h-80 bg-gradient-to-br from-blue-400 to-purple-600 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-pulse"
        style="animation-duration: 5s;"
      />
      <div
        class="absolute -top-40 -left-40 w-80 h-80 bg-gradient-to-br from-pink-400 to-red-600 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-pulse"
        style="animation-duration: 7s; animation-delay: 1.5s;"
      />
      <div
        class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-96 h-96 bg-gradient-to-br from-yellow-400 to-orange-600 rounded-full mix-blend-multiply filter blur-xl opacity-10 animate-pulse"
        style="animation-duration: 9s; animation-delay: 3s;"
      />
    </div>

    <!-- Container -->
    <div class="relative z-10 container mx-auto">
      <!-- Section Header -->
      <div class="text-center mb-20 relative">
        <!-- Decorative Background -->
        <div class="absolute inset-0 flex items-center justify-center">
          <div class="w-32 h-32 bg-gradient-to-r from-blue-500/10 to-purple-500/10 rounded-full blur-3xl"></div>
        </div>
        
        <!-- Main Content -->
        <div class="relative z-10">
          <!-- Badge -->
          <div class="inline-flex items-center px-6 py-3 rounded-full bg-gradient-to-r from-blue-100 to-purple-100 dark:from-blue-900/30 dark:to-purple-900/30 border border-blue-200 dark:border-blue-700 mb-6">
            <Icon icon="mdi:code-braces" class="text-xl text-blue-600 dark:text-blue-400 mr-2" />
            <span class="text-sm font-semibold text-blue-700 dark:text-blue-300">ทักษะของผม</span>
          </div>
          
          <!-- Main Title -->
          <h2 class="text-5xl md:text-6xl lg:text-7xl font-black mb-6">
            <span class="bg-gradient-to-r from-blue-600 via-purple-600 to-pink-600 bg-clip-text text-transparent">
              ทักษะที่เชี่ยวชาญ
            </span>
          </h2>
          
          <!-- Subtitle -->
          <div class="flex items-center justify-center space-x-4 mb-6">
            <div class="w-12 h-0.5 bg-gradient-to-r from-transparent to-blue-500 rounded-full"></div>
            <p class="text-xl md:text-2xl text-slate-600 dark:text-slate-300 font-medium">
              เทคโนโลยีที่ผมใช้ได้
            </p>
            <div class="w-12 h-0.5 bg-gradient-to-r from-purple-500 to-transparent rounded-full"></div>
          </div>
          
          <!-- Description -->
          <p class="text-lg text-slate-500 dark:text-slate-400 max-w-2xl mx-auto leading-relaxed">
            ทักษะด้านเทคโนโลยีที่หลากหลาย เพื่อสร้างสรรค์ผลงานที่ยอดเยี่ยม
          </p>
        </div>
        
        <!-- Bottom Decoration -->
        <div class="absolute -bottom-8 left-1/2 transform -translate-x-1/2 flex items-center space-x-3">
          <div class="w-2 h-2 bg-blue-400 rounded-full animate-pulse"></div>
          <div class="w-16 h-0.5 bg-gradient-to-r from-blue-400 via-purple-400 to-pink-400 rounded-full"></div>
          <div class="w-2 h-2 bg-purple-400 rounded-full animate-pulse" style="animation-delay: 0.5s"></div>
          <div class="w-16 h-0.5 bg-gradient-to-r from-purple-400 via-pink-400 to-orange-400 rounded-full"></div>
          <div class="w-2 h-2 bg-pink-400 rounded-full animate-pulse" style="animation-delay: 1s"></div>
        </div>
      </div>

      <!-- Skills Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <div
          v-for="skill in skills"
          :key="skill.id"
          class="group relative overflow-hidden"
          data-aos="fade-up"
          :data-aos-delay="skill.id * 100"
        >
          <!-- Skill Card -->
          <div class="relative bg-white/90 dark:bg-slate-800/90 backdrop-blur-sm rounded-3xl p-8 text-center border border-slate-200/60 dark:border-slate-700/60 shadow-lg hover:shadow-2xl transition-all duration-500 hover:scale-105">
            
            <!-- Background Gradient -->
            <div 
              :class="`absolute inset-0 bg-gradient-to-br ${skill.bgColor} opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
            />
            
            <!-- Floating Elements -->
            <div class="absolute -top-2 -right-2 w-4 h-4 bg-blue-400/30 rounded-full group-hover:animate-ping" />
            <div class="absolute -bottom-2 -left-2 w-3 h-3 bg-purple-400/30 rounded-full group-hover:animate-ping" style="animation-delay: 0.5s" />
            
            <!-- Icon Container -->
            <div class="relative z-10 mb-6">
              <div 
                :class="`w-20 h-20 mx-auto rounded-3xl bg-gradient-to-br ${skill.color} flex items-center justify-center shadow-lg group-hover:scale-110 group-hover:rotate-3 transition-all duration-500`"
              >
                <Icon 
                  :icon="skill.icon" 
                  class="text-3xl text-white group-hover:animate-bounce" 
                />
              </div>
              
              <!-- Icon Glow -->
              <div 
                :class="`absolute inset-0 w-20 h-20 mx-auto rounded-3xl bg-gradient-to-br ${skill.color} opacity-0 group-hover:opacity-30 blur-xl transition-opacity duration-500`"
              />
            </div>

            <!-- Percentage Display -->
            <div class="relative z-10 mb-6">
              <div class="flex items-center justify-center space-x-2 mb-2">
                <span class="text-4xl lg:text-5xl font-black text-slate-800 dark:text-white group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-blue-600 group-hover:to-purple-600 group-hover:bg-clip-text transition-all duration-500">
                  <CountUp 
                    v-if="hasIntersected" 
                    :endVal="skill.percentage" 
                    :duration="2.5"
                    :delay="0.2"
                  />
                </span>
                <span class="text-2xl lg:text-3xl font-bold text-slate-600 dark:text-slate-400 group-hover:text-blue-500 transition-colors duration-500">
                  %
                </span>
              </div>
            </div>

            <!-- Content -->
            <div class="relative z-10">
              <!-- Title -->
              <h3 class="text-lg font-bold text-slate-800 dark:text-white mb-2 group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-blue-600 group-hover:to-purple-600 group-hover:bg-clip-text transition-all duration-500">
                {{ skill.name }}
            </h3>
              
              <!-- Description -->
              <p class="text-sm text-slate-500 dark:text-slate-400 mb-3">
                {{ skill.description }}
              </p>
              
              <!-- Level Badge -->
              <div class="flex items-center justify-center">
                <span 
                  :class="`px-3 py-1 rounded-full text-xs font-semibold bg-gradient-to-r ${skill.color} text-white`"
                >
                  {{ skill.level }}
                </span>
              </div>
            </div>

            <!-- Bottom Accent -->
            <div 
              :class="`absolute bottom-0 left-1/2 transform -translate-x-1/2 w-16 h-1 bg-gradient-to-r ${skill.color} rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
            />
          </div>
        </div>
        </div>
    </div>
  </section>
</template>

<style scoped></style>
