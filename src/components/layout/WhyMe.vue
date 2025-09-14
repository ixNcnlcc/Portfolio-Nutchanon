<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import Education from "@/components/layout/Education.vue";
import Experience from "@/components/layout/Experience.vue";

// Constants
const OBSERVER_THRESHOLD = 0.3;

// Why Me data
const whyMePoints = ref([
  {
    id: 1,
    title: "ความมุ่งมั่น",
    description: "ผมมีความมุ่งมั่นในการเรียนรู้และพัฒนาตัวเองอย่างต่อเนื่อง เพื่อให้ได้ผลงานที่มีคุณภาพสูงสุด",
    icon: "mdi:target",
    color: "from-blue-500 to-cyan-500",
    bgColor: "from-blue-50 to-cyan-50 dark:from-blue-900/20 dark:to-cyan-900/20",
    borderColor: "border-blue-200 dark:border-blue-700"
  },
  {
    id: 2,
    title: "ความคิดสร้างสรรค์",
    description: "มีความคิดสร้างสรรค์และแนวทางใหม่ๆ ในการแก้ปัญหา เพื่อสร้างผลงานที่โดดเด่นและแตกต่าง",
    icon: "mdi:lightbulb-on",
    color: "from-yellow-500 to-orange-500",
    bgColor: "from-yellow-50 to-orange-50 dark:from-yellow-900/20 dark:to-orange-900/20",
    borderColor: "border-yellow-200 dark:border-yellow-700"
  },
  {
    id: 3,
    title: "การทำงานเป็นทีม",
    description: "สามารถทำงานร่วมกับทีมได้อย่างมีประสิทธิภาพ และสื่อสารได้ดีกับทุกคนในทีม",
    icon: "mdi:account-group",
    color: "from-green-500 to-emerald-500",
    bgColor: "from-green-50 to-emerald-50 dark:from-green-900/20 dark:to-emerald-900/20",
    borderColor: "border-green-200 dark:border-green-700"
  },
  {
    id: 4,
    title: "ความรับผิดชอบ",
    description: "มีความรับผิดชอบสูงในการทำงาน และมุ่งมั่นที่จะส่งมอบผลงานตรงเวลาและมีคุณภาพ",
    icon: "mdi:shield-check",
    color: "from-purple-500 to-pink-500",
    bgColor: "from-purple-50 to-pink-50 dark:from-purple-900/20 dark:to-pink-900/20",
    borderColor: "border-purple-200 dark:border-purple-700"
  }
]);

// Reactive state
const whyMeSection = ref(null);
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

  if (whyMeSection.value) {
    observer.observe(whyMeSection.value);
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
    ref="whyMeSection"
    class="relative py-20 px-4 overflow-hidden"
    id="why-me"
  >
    <!-- Background Elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div
        class="absolute -top-40 -right-40 w-80 h-80 bg-gradient-to-br from-blue-400 to-purple-600 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-pulse"
        style="animation-duration: 5s;"
      />
      <div
        class="absolute -bottom-40 -left-40 w-80 h-80 bg-gradient-to-br from-pink-400 to-red-600 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-pulse"
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
            <Icon icon="mdi:star" class="text-xl text-blue-600 dark:text-blue-400 mr-2" />
            <span class="text-sm font-semibold text-blue-700 dark:text-blue-300">ทำไมต้องเลือกผม</span>
          </div>
          
          <!-- Main Title -->
          <h2 class="text-5xl md:text-6xl lg:text-7xl font-black mb-6">
            <span class="bg-gradient-to-r from-blue-600 via-purple-600 to-pink-600 bg-clip-text text-transparent">
              ทำไมต้องเลือกผม?
            </span>
          </h2>
          
          <!-- Subtitle -->
          <div class="flex items-center justify-center space-x-4 mb-6">
            <div class="w-12 h-0.5 bg-gradient-to-r from-transparent to-blue-500 rounded-full"></div>
            <p class="text-xl md:text-2xl text-slate-600 dark:text-slate-300 font-medium">
              จุดเด่นที่ทำให้ผมแตกต่าง
            </p>
            <div class="w-12 h-0.5 bg-gradient-to-r from-purple-500 to-transparent rounded-full"></div>
          </div>
          
          <!-- Description -->
          <p class="text-lg text-slate-500 dark:text-slate-400 max-w-2xl mx-auto leading-relaxed">
            คุณสมบัติและจุดเด่นที่ทำให้ผมเป็นตัวเลือกที่ดีสำหรับโปรเจกต์ของคุณ
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

      <!-- Why Me Points Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-16">
        <div
          v-for="point in whyMePoints"
          :key="point.id"
          class="group relative overflow-hidden"
          data-aos="fade-up"
          :data-aos-delay="point.id * 100"
        >
          <!-- Point Card -->
          <div class="relative bg-white/90 dark:bg-slate-800/90 backdrop-blur-sm rounded-3xl p-8 border border-slate-200/60 dark:border-slate-700/60 shadow-lg hover:shadow-2xl transition-all duration-500 hover:scale-105">
            
            <!-- Background Gradient -->
            <div 
              :class="`absolute inset-0 bg-gradient-to-br ${point.bgColor} opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
            />
            
            <!-- Floating Elements -->
            <div class="absolute -top-2 -right-2 w-4 h-4 bg-blue-400/30 rounded-full group-hover:animate-ping" />
            <div class="absolute -bottom-2 -left-2 w-3 h-3 bg-purple-400/30 rounded-full group-hover:animate-ping" style="animation-delay: 0.5s" />
            
            <!-- Icon Container -->
            <div class="relative z-10 mb-6">
              <div 
                :class="`w-16 h-16 mx-auto rounded-2xl bg-gradient-to-br ${point.color} flex items-center justify-center shadow-lg group-hover:scale-110 group-hover:rotate-3 transition-all duration-500`"
              >
                <Icon 
                  :icon="point.icon" 
                  class="text-2xl text-white group-hover:animate-bounce" 
                />
              </div>
              
              <!-- Icon Glow -->
              <div 
                :class="`absolute inset-0 w-16 h-16 mx-auto rounded-2xl bg-gradient-to-br ${point.color} opacity-0 group-hover:opacity-30 blur-xl transition-opacity duration-500`"
              />
            </div>

            <!-- Content -->
            <div class="relative z-10">
              <!-- Title -->
              <h3 class="text-xl font-bold text-slate-800 dark:text-white mb-4 group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-blue-600 group-hover:to-purple-600 group-hover:bg-clip-text transition-all duration-500">
                {{ point.title }}
              </h3>
              
              <!-- Description -->
              <p class="text-slate-600 dark:text-slate-300 leading-relaxed">
                {{ point.description }}
              </p>
            </div>

            <!-- Bottom Accent -->
            <div 
              :class="`absolute bottom-0 left-1/2 transform -translate-x-1/2 w-16 h-1 bg-gradient-to-r ${point.color} rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
            />
          </div>
        </div>
      </div>

      <!-- Education & Experience Section -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        <div data-aos="fade-left">
          <Education />
        </div>
        <div data-aos="fade-right">
          <Experience />
        </div>
      </div>
    </div>
  </section>
</template>