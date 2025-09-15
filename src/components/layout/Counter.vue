<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import CountUp from "vue-countup-v3";

// Constants
const OBSERVER_THRESHOLD = 0.1; // Lower threshold for mobile

// Stats data with enhanced properties
const stats = ref([
  { 
    id: 1, 
    number: 5, 
    title: "โปรเจกต์ที่ทำเสร็จ", 
    suffix: "ชิ้น",
    icon: "mdi:rocket-launch",
    color: "from-blue-500 to-cyan-500",
    bgColor: "from-blue-50 to-cyan-50 dark:from-blue-900/20 dark:to-cyan-900/20",
    borderColor: "border-blue-200 dark:border-blue-700",
    description: "โปรเจกต์ที่สำเร็จแล้ว",
    trend: "+2 เปอร์เซ็นต์"
  },
  { 
    id: 2, 
    number: 4, 
    title: "เทคโนโลยีที่เชี่ยวชาญ", 
    suffix: "ประเภท",
    icon: "mdi:code-braces",
    color: "from-purple-500 to-pink-500",
    bgColor: "from-purple-50 to-pink-50 dark:from-purple-900/20 dark:to-pink-900/20",
    borderColor: "border-purple-200 dark:border-purple-700",
    description: "เทคโนโลยีที่เชี่ยวชาญ",
    trend: "+1 เปอร์เซ็นต์"
  },
  { 
    id: 3, 
    number: 25, 
    title: "ลูกค้าที่พอใจ", 
    suffix: "คน",
    icon: "mdi:heart",
    color: "from-green-500 to-emerald-500",
    bgColor: "from-green-50 to-emerald-50 dark:from-green-900/20 dark:to-emerald-900/20",
    borderColor: "border-green-200 dark:border-green-700",
    description: "ลูกค้าที่พอใจในงาน",
    trend: "+5 เปอร์เซ็นต์"
  },
  { 
    id: 4, 
    number: 1, 
    title: "ฝึกฝนด้วยตัวเองเป็นเวลา", 
    suffix: "ปี",
    icon: "mdi:clock",
    color: "from-orange-500 to-red-500",
    bgColor: "from-orange-50 to-red-50 dark:from-orange-900/20 dark:to-red-900/20",
    borderColor: "border-orange-200 dark:border-orange-700",
    description: "เวลาที่ใช้ในการเรียนรู้",
    trend: "+100 เปอร์เซ็นต์"
  },
]);

// Reactive state
const statsSection = ref(null);
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
    { 
      threshold: OBSERVER_THRESHOLD,
      rootMargin: '0px 0px -50px 0px' // Trigger earlier on mobile
    }
    );

  if (statsSection.value) {
        observer.observe(statsSection.value);
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
    ref="statsSection"
    class="relative py-20 px-4 overflow-hidden"
  >
    <!-- Background Elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div
        class="absolute -bottom-40 -right-40 w-80 h-80 bg-gradient-to-br from-blue-400 to-purple-600 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-pulse"
        style="animation-duration: 5s;"
      />
      <div
        class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-96 h-96 bg-gradient-to-br from-yellow-400 to-orange-600 rounded-full mix-blend-multiply filter blur-xl opacity-10 animate-pulse"
        style="animation-duration: 9s; animation-delay: 3s;"
      />
      <!-- Additional Pink-Red Orb (Top Left) -->
      <div
        class="absolute -top-40 -left-40 w-80 h-80 bg-gradient-to-br from-pink-400 to-red-600 rounded-full mix-blend-multiply filter blur-xl opacity-25 animate-pulse"
        style="animation-duration: 6s; animation-delay: 0.5s;"
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
            <Icon icon="mdi:chart-line" class="text-xl text-blue-600 dark:text-blue-400 mr-2" />
            <span class="text-sm font-semibold text-blue-700 dark:text-blue-300">สถิติผลงาน</span>
          </div>
          
          <!-- Main Title -->
          <h2 class="text-5xl md:text-6xl lg:text-7xl font-black mb-6">
            <span class="bg-gradient-to-r from-blue-600 via-purple-600 to-pink-600 bg-clip-text text-transparent">
              ผลงานของผม
            </span>
          </h2>
          
          <!-- Subtitle -->
          <div class="flex items-center justify-center space-x-4 mb-6">
            <div class="w-12 h-0.5 bg-gradient-to-r from-transparent to-blue-500 rounded-full"></div>
            <p class="text-xl md:text-2xl text-slate-600 dark:text-slate-300 font-medium">
              ตัวเลขที่บอกเล่าเรื่องราว
            </p>
            <div class="w-12 h-0.5 bg-gradient-to-r from-purple-500 to-transparent rounded-full"></div>
          </div>
          
          <!-- Description -->
          <p class="text-lg text-slate-500 dark:text-slate-400 max-w-2xl mx-auto leading-relaxed">
            เรื่องราวการทำงานและประสบการณ์ที่สะสมมาผ่านตัวเลขเหล่านี้
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

      <!-- Stats Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <div
          v-for="stat in stats"
          :key="stat.id"
          class="group relative overflow-hidden"
          data-aos="fade-up"
          :data-aos-delay="stat.id * 100"
        >
          <!-- Card Container -->
          <div class="relative bg-white/90 dark:bg-slate-800/90 backdrop-blur-sm rounded-3xl p-8 text-center border border-slate-200/60 dark:border-slate-700/60 shadow-lg hover:shadow-2xl transition-all duration-500 hover:scale-105">
            
            <!-- Background Gradient -->
            <div 
              :class="`absolute inset-0 bg-gradient-to-br ${stat.bgColor} opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
            />
            
            <!-- Floating Elements -->
            <div class="absolute -top-2 -right-2 w-4 h-4 bg-blue-400/30 rounded-full group-hover:animate-ping" />
            <div class="absolute -bottom-2 -left-2 w-3 h-3 bg-purple-400/30 rounded-full group-hover:animate-ping" style="animation-delay: 0.5s" />
            
            <!-- Icon Container -->
            <div class="relative z-10 mb-6">
              <div 
                :class="`w-20 h-20 mx-auto rounded-3xl bg-gradient-to-br ${stat.color} flex items-center justify-center shadow-lg group-hover:scale-110 group-hover:rotate-3 transition-all duration-500`"
              >
                <Icon 
                  :icon="stat.icon" 
                  class="text-3xl text-white group-hover:animate-bounce" 
                />
              </div>
              
              <!-- Icon Glow -->
              <div 
                :class="`absolute inset-0 w-20 h-20 mx-auto rounded-3xl bg-gradient-to-br ${stat.color} opacity-0 group-hover:opacity-30 blur-xl transition-opacity duration-500`"
              />
            </div>

            <!-- Number Display -->
            <div class="relative z-10 mb-6">
              <div class="flex items-center justify-center space-x-2 mb-2">
                <span class="text-5xl lg:text-6xl font-black text-slate-800 dark:text-white group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-blue-600 group-hover:to-purple-600 group-hover:bg-clip-text transition-all duration-500">
                  <CountUp 
                    v-if="hasIntersected" 
                    :endVal="stat.number" 
                    :duration="2.5"
                    :delay="0.2"
                  />
                  <span v-else class="text-5xl lg:text-6xl font-black">{{ stat.number }}</span>
                </span>
                <span class="text-3xl lg:text-4xl font-bold text-slate-600 dark:text-slate-400 group-hover:text-blue-500 transition-colors duration-500">
                  {{ stat.suffix }}
                </span>
              </div>
              
              <!-- Plus Symbol -->
              <div class="absolute -top-2 -right-2">
                <span class="text-xl font-bold bg-gradient-to-r from-blue-500 to-purple-500 bg-clip-text text-transparent group-hover:scale-125 transition-transform duration-500">
                  +
                </span>
              </div>
            </div>

            <!-- Content -->
            <div class="relative z-10">
              <!-- Title -->
              <h3 class="text-lg font-bold text-slate-800 dark:text-white mb-2 group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-blue-600 group-hover:to-purple-600 group-hover:bg-clip-text transition-all duration-500">
                {{ stat.title }}
              </h3>
              
              <!-- Description -->
              <p class="text-sm text-slate-500 dark:text-slate-400 mb-3">
                {{ stat.description }}
              </p>
              
              <!-- Trend -->
              <div class="flex items-center justify-center space-x-1">
                <Icon icon="mdi:trending-up" class="text-green-500 text-sm" />
                <span class="text-xs font-semibold text-green-600 dark:text-green-400">
                  {{ stat.trend }}
                </span>
              </div>
            </div>

            <!-- Bottom Accent -->
            <div 
              :class="`absolute bottom-0 left-1/2 transform -translate-x-1/2 w-16 h-1 bg-gradient-to-r ${stat.color} rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
