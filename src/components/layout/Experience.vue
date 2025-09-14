<script setup>
import { ref, onMounted, onUnmounted } from "vue";

// Constants
const OBSERVER_THRESHOLD = 0.3;

// Experience data
const experience = ref([
  {
    id: 1,
    duration: "2024 - Present",
    title: "Frontend Developer",
    workplace: "มหาวิทยาลัยราชภัฏสวนสุนันทา",
    duties: "ออกแบบและพัฒนาเว็บไซต์ให้กับกองพัฒนานักศึกษา สำหรับงานรับพระราชทานปริญญาบัตร",
    type: "งานประจำ",
    status: "กำลังทำงาน",
    icon: "mdi:briefcase",
    color: "from-green-500 to-emerald-500",
    bgColor: "from-green-50 to-emerald-50 dark:from-green-900/20 dark:to-emerald-900/20",
    borderColor: "border-green-200 dark:border-green-700",
    description: "พัฒนาเว็บแอปพลิเคชันสำหรับงานสำคัญของมหาวิทยาลัย ใช้เทคโนโลยี Vue.js, Tailwind CSS และ JavaScript"
  },
  {
    id: 2,
    duration: "2024",
    title: "Frontend Developer",
    workplace: "Work from Home",
    duties: "ออกแบบ Portfolio Website",
    type: "โปรเจกต์ส่วนตัว",
    status: "เสร็จสิ้น",
    icon: "mdi:laptop",
    color: "from-purple-500 to-pink-500",
    bgColor: "from-purple-50 to-pink-50 dark:from-purple-900/20 dark:to-pink-900/20",
    borderColor: "border-purple-200 dark:border-purple-700",
    description: "ออกแบบและพัฒนาเว็บไซต์ Portfolio เพื่อแสดงผลงานและทักษะในการพัฒนาเว็บ"
  },
  {
    id: 3,
    duration: "2024",
    title: "Frontend Developer",
    workplace: "Work from Home",
    duties: "ออกแบบเว็บไซต์สำหรับเก็บผลงาน",
    type: "โปรเจกต์ส่วนตัว",
    status: "เสร็จสิ้น",
    icon: "mdi:folder-multiple",
    color: "from-orange-500 to-red-500",
    bgColor: "from-orange-50 to-red-50 dark:from-orange-900/20 dark:to-red-900/20",
    borderColor: "border-orange-200 dark:border-orange-700",
    description: "สร้างเว็บไซต์สำหรับจัดเก็บและแสดงผลงานต่างๆ พร้อมระบบจัดการเนื้อหา"
  }
]);

// Reactive state
const experienceSection = ref(null);
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

  if (experienceSection.value) {
    observer.observe(experienceSection.value);
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
  <div ref="experienceSection" class="relative">
    <!-- Header -->
    <div class="text-center mb-12 relative">
      <!-- Decorative Background -->
      <div class="absolute inset-0 flex items-center justify-center">
        <div class="w-24 h-24 bg-gradient-to-r from-green-500/10 to-emerald-500/10 rounded-full blur-2xl"></div>
      </div>
      
      <!-- Main Content -->
      <div class="relative z-10">
        <!-- Badge -->
        <div class="inline-flex items-center px-4 py-2 rounded-full bg-gradient-to-r from-green-100 to-emerald-100 dark:from-green-900/30 dark:to-emerald-900/30 border border-green-200 dark:border-green-700 mb-4">
          <Icon icon="mdi:briefcase" class="text-lg text-green-600 dark:text-green-400 mr-2" />
          <span class="text-sm font-semibold text-green-700 dark:text-green-300">ประสบการณ์</span>
        </div>
        
        <!-- Main Title -->
        <h3 class="text-3xl md:text-4xl font-black mb-4">
          <span class="bg-gradient-to-r from-green-600 to-emerald-600 bg-clip-text text-transparent">
            ประสบการณ์การทำงาน
          </span>
        </h3>
        
        <!-- Description -->
        <p class="text-slate-600 dark:text-slate-400 max-w-xl mx-auto">
          ประสบการณ์การพัฒนาเว็บแอปพลิเคชันและโปรเจกต์ต่างๆ
        </p>
      </div>
    </div>

    <!-- Experience Timeline -->
    <div class="relative">
      <!-- Timeline Line -->
      <div class="absolute left-8 top-0 bottom-0 w-0.5 bg-gradient-to-b from-green-500 via-emerald-500 to-purple-500"></div>
      
      <!-- Experience Items -->
      <div class="space-y-8">
        <div
          v-for="(item, index) in experience"
          :key="item.id"
          class="relative group"
          data-aos="fade-left"
          :data-aos-delay="index * 200"
        >
          <!-- Timeline Dot -->
          <div class="absolute left-6 w-4 h-4 bg-white dark:bg-slate-800 rounded-full border-4 border-green-500 z-10 group-hover:scale-125 transition-transform duration-300">
            <div class="w-full h-full rounded-full bg-gradient-to-r from-green-500 to-emerald-500"></div>
          </div>
          
          <!-- Experience Card -->
          <div class="ml-16 relative">
            <div class="relative bg-white/90 dark:bg-slate-800/90 backdrop-blur-sm rounded-2xl p-6 border border-slate-200/60 dark:border-slate-700/60 shadow-lg hover:shadow-2xl transition-all duration-500 hover:scale-105">
              
              <!-- Background Gradient -->
              <div 
                :class="`absolute inset-0 bg-gradient-to-br ${item.bgColor} opacity-0 group-hover:opacity-100 transition-opacity duration-500 rounded-2xl`"
              />
              
              <!-- Floating Elements -->
              <div class="absolute -top-2 -right-2 w-3 h-3 bg-green-400/30 rounded-full group-hover:animate-ping" />
              <div class="absolute -bottom-2 -left-2 w-2 h-2 bg-emerald-400/30 rounded-full group-hover:animate-ping" style="animation-delay: 0.5s" />
              
              <!-- Content -->
              <div class="relative z-10">
                <!-- Header -->
                <div class="flex items-start justify-between mb-4">
                  <div class="flex items-center space-x-3">
                    <!-- Icon -->
                    <div 
                      :class="`w-12 h-12 rounded-xl bg-gradient-to-br ${item.color} flex items-center justify-center shadow-lg group-hover:scale-110 group-hover:rotate-3 transition-all duration-500`"
                    >
                      <Icon 
                        :icon="item.icon" 
                        class="text-xl text-white group-hover:animate-bounce" 
                      />
                    </div>
                    
                    <!-- Title & Status -->
                    <div>
                      <h4 class="text-lg font-bold text-slate-800 dark:text-white group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-green-600 group-hover:to-emerald-600 group-hover:bg-clip-text transition-all duration-500">
                        {{ item.title }}
                      </h4>
                      <div class="flex items-center space-x-2">
                        <span 
                          :class="`px-2 py-1 rounded-full text-xs font-semibold bg-gradient-to-r ${item.color} text-white`"
                        >
                          {{ item.status }}
                        </span>
                        <span class="text-sm text-slate-500 dark:text-slate-400">
                          {{ item.type }}
                        </span>
                      </div>
                    </div>
                  </div>
                  
                  <!-- Duration -->
                  <div class="text-right">
                    <span class="text-sm font-semibold text-slate-600 dark:text-slate-400 bg-slate-100 dark:bg-slate-700 px-3 py-1 rounded-full">
                      {{ item.duration }}
                    </span>
                  </div>
                </div>
                
                <!-- Details -->
                <div class="space-y-3">
                  <div class="text-slate-700 dark:text-slate-300 font-medium">
                    {{ item.workplace }}
                  </div>
                  <div class="text-slate-600 dark:text-slate-400 font-semibold">
                    {{ item.duties }}
                  </div>
                  <p class="text-sm text-slate-500 dark:text-slate-400 leading-relaxed">
                    {{ item.description }}
                  </p>
                </div>
                
                <!-- Bottom Accent -->
                <div 
                  :class="`absolute bottom-0 left-0 right-0 h-1 bg-gradient-to-r ${item.color} rounded-b-2xl opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
