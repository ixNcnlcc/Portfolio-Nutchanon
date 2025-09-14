<script setup>
import { ref, onMounted, onUnmounted } from "vue";

// Constants
const OBSERVER_THRESHOLD = 0.3;

// Education data
const education = ref([
  {
    id: 1,
    duration: "2022 - Present",
    university: "มหาวิทยาลัยราชภัฏสวนสุนันทา",
    faculty: "คณะวิศวกรรมศาสตร์และเทคโนโลยีอุตสาหกรรม",
    major: "วิศวกรรมคอมพิวเตอร์",
    degree: "ปริญญาตรี",
    status: "กำลังศึกษา",
    icon: "mdi:school",
    color: "from-blue-500 to-cyan-500",
    bgColor: "from-blue-50 to-cyan-50 dark:from-blue-900/20 dark:to-cyan-900/20",
    borderColor: "border-blue-200 dark:border-blue-700",
    description: "การศึกษาด้านวิศวกรรมคอมพิวเตอร์ เน้นการพัฒนาเว็บแอปพลิเคชันและระบบซอฟต์แวร์"
  },
  {
    id: 2,
    duration: "2015 - 2019",
    university: "มหาวิทยาลัยมหาสารคาม",
    faculty: "คณะวิศวกรรมศาสตร์",
    major: "วิศวกรรมชีวภาพและอาหาร",
    degree: "ปริญญาตรี",
    status: "จบการศึกษา",
    icon: "mdi:graduation-cap",
    color: "from-green-500 to-emerald-500",
    bgColor: "from-green-50 to-emerald-50 dark:from-green-900/20 dark:to-emerald-900/20",
    borderColor: "border-green-200 dark:border-green-700",
    description: "การศึกษาด้านวิศวกรรมชีวภาพและอาหาร เรียนรู้การประยุกต์ใช้เทคโนโลยีในอุตสาหกรรมอาหาร"
  },
  {
    id: 3,
    duration: "2012 - 2015",
    school: "โรงเรียนนครพนมวิทยาคม",
    major: "มัธยมศึกษาปีที่ 6",
    degree: "มัธยมปลาย",
    status: "จบการศึกษา",
    icon: "mdi:book-open",
    color: "from-purple-500 to-pink-500",
    bgColor: "from-purple-50 to-pink-50 dark:from-purple-900/20 dark:to-pink-900/20",
    borderColor: "border-purple-200 dark:border-purple-700",
    description: "การศึกษาระดับมัธยมปลาย เน้นวิทยาศาสตร์และคณิตศาสตร์"
  }
]);

// Reactive state
const educationSection = ref(null);
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

  if (educationSection.value) {
    observer.observe(educationSection.value);
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
  <div ref="educationSection" class="relative">
    <!-- Header -->
    <div class="text-center mb-12 relative">
      <!-- Decorative Background -->
      <div class="absolute inset-0 flex items-center justify-center">
        <div class="w-24 h-24 bg-gradient-to-r from-blue-500/10 to-cyan-500/10 rounded-full blur-2xl"></div>
      </div>
      
      <!-- Main Content -->
      <div class="relative z-10">
        <!-- Badge -->
        <div class="inline-flex items-center px-4 py-2 rounded-full bg-gradient-to-r from-blue-100 to-cyan-100 dark:from-blue-900/30 dark:to-cyan-900/30 border border-blue-200 dark:border-blue-700 mb-4">
          <Icon icon="mdi:school" class="text-lg text-blue-600 dark:text-blue-400 mr-2" />
          <span class="text-sm font-semibold text-blue-700 dark:text-blue-300">การศึกษา</span>
        </div>
        
        <!-- Main Title -->
        <h3 class="text-3xl md:text-4xl font-black mb-4">
          <span class="bg-gradient-to-r from-blue-600 to-cyan-600 bg-clip-text text-transparent">
            ประวัติการศึกษา
          </span>
        </h3>
        
        <!-- Description -->
        <p class="text-slate-600 dark:text-slate-400 max-w-xl mx-auto">
          การศึกษาที่หลากหลายและครอบคลุมทั้งด้านวิศวกรรมและเทคโนโลยี
        </p>
      </div>
    </div>

    <!-- Education Timeline -->
    <div class="relative">
      <!-- Timeline Line -->
      <div class="absolute left-8 top-0 bottom-0 w-0.5 bg-gradient-to-b from-blue-500 via-cyan-500 to-purple-500"></div>
      
      <!-- Education Items -->
      <div class="space-y-8">
        <div
          v-for="(item, index) in education"
          :key="item.id"
          class="relative group"
          data-aos="fade-right"
          :data-aos-delay="index * 200"
        >
          <!-- Timeline Dot -->
          <div class="absolute left-6 w-4 h-4 bg-white dark:bg-slate-800 rounded-full border-4 border-blue-500 z-10 group-hover:scale-125 transition-transform duration-300">
            <div class="w-full h-full rounded-full bg-gradient-to-r from-blue-500 to-cyan-500"></div>
          </div>
          
          <!-- Education Card -->
          <div class="ml-16 relative">
            <div class="relative bg-white/90 dark:bg-slate-800/90 backdrop-blur-sm rounded-2xl p-6 border border-slate-200/60 dark:border-slate-700/60 shadow-lg hover:shadow-2xl transition-all duration-500 hover:scale-105">
              
              <!-- Background Gradient -->
              <div 
                :class="`absolute inset-0 bg-gradient-to-br ${item.bgColor} opacity-0 group-hover:opacity-100 transition-opacity duration-500 rounded-2xl`"
              />
              
              <!-- Floating Elements -->
              <div class="absolute -top-2 -right-2 w-3 h-3 bg-blue-400/30 rounded-full group-hover:animate-ping" />
              <div class="absolute -bottom-2 -left-2 w-2 h-2 bg-cyan-400/30 rounded-full group-hover:animate-ping" style="animation-delay: 0.5s" />
              
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
                      <h4 class="text-lg font-bold text-slate-800 dark:text-white group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-blue-600 group-hover:to-cyan-600 group-hover:bg-clip-text transition-all duration-500">
                        {{ item.university || item.school }}
                      </h4>
                      <div class="flex items-center space-x-2">
                        <span 
                          :class="`px-2 py-1 rounded-full text-xs font-semibold bg-gradient-to-r ${item.color} text-white`"
                        >
                          {{ item.status }}
                        </span>
                        <span class="text-sm text-slate-500 dark:text-slate-400">
                          {{ item.degree }}
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
                <div class="space-y-2">
                  <div v-if="item.faculty" class="text-slate-700 dark:text-slate-300 font-medium">
                    {{ item.faculty }}
                  </div>
                  <div class="text-slate-600 dark:text-slate-400 font-semibold">
                    {{ item.major }}
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
