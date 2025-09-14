<script setup>
import { ref, onMounted, onUnmounted } from "vue";

// Constants
const OBSERVER_THRESHOLD = 0.3;

// Projects data
const projects = ref([
  {
    id: 1,
    title: "Portfolio Website",
    description: "เว็บไซต์ Portfolio ที่แสดงผลงานและทักษะในการพัฒนาเว็บ พร้อมระบบจัดการเนื้อหาและ responsive design",
    image: 'https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=600&h=400&fit=crop',
    tags: ['Vue.js', 'Tailwind CSS', 'JavaScript', 'Responsive'],
    liveLink: '/',
    codeLink: "https://github.com",
    status: "เสร็จสิ้น",
    year: "2025",
    icon: "mdi:web",
    color: "from-blue-500 to-cyan-500",
    bgColor: "from-blue-50 to-cyan-50 dark:from-blue-900/20 dark:to-cyan-900/20",
    borderColor: "border-blue-200 dark:border-blue-700"
  },
  {
    id: 2,
    title: "Project RFID website",
    description: "ระบบตรวจสอบรายชื่อบัณฑิตออนไลน์ที่พัฒนาด้วย Vue.js และ Tailwind CSS พร้อมระบบแสดงสถานะผ่านที่นั่งแบบเรียลไทม์",
    image: '/images/degree3.jpg', // ใส่รูปโปรเจกต์ของคุณใน public/images/
    tags: ['Vue.js', 'Tailwind CSS', 'JavaScript', 'Booking System'],
    liveLink: 'http://27.254.134.124/uikit/Seat',
    codeLink: "https://github.com/ixNcnlcc/Project_RFID/tree/mic", // ใส่ GitHub URL ของคุณ
    status: "กำลังพัฒนา",
    year: "2025",
    icon: "mdi:seat",
    color: "from-orange-500 to-red-500",
    bgColor: "from-orange-50 to-red-50 dark:from-orange-900/20 dark:to-red-900/20",
    borderColor: "border-orange-200 dark:border-orange-700"
  },
  {
    id: 3,
    title: "E-Commerce Website",
    description: "เว็บไซต์ขายของออนไลน์ที่มีระบบจัดการสินค้า ตะกร้าสินค้า และระบบชำระเงิน",
    image: 'https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?w=600&h=400&fit=crop',
    tags: ['Vue.js', 'Tailwind CSS', 'API', 'Payment'],
    liveLink: 'https://example.com',
    codeLink: "https://github.com",
    status: "กำลังพัฒนา",
    year: "2025",
    icon: "mdi:shopping",
    color: "from-green-500 to-emerald-500",
    bgColor: "from-green-50 to-emerald-50 dark:from-green-900/20 dark:to-emerald-900/20",
    borderColor: "border-green-200 dark:border-green-700"
  },
  {
    id: 4,
    title: "Task Management App",
    description: "แอปพลิเคชันจัดการงานที่มีระบบแจ้งเตือน ติดตามความคืบหน้า และการทำงานเป็นทีม",
    image: 'https://images.unsplash.com/photo-1611224923853-80b023f02d71?w=600&h=400&fit=crop',
    tags: ['Vue.js', 'Tailwind CSS', 'LocalStorage', 'PWA'],
    liveLink: 'https://example.com',
    codeLink: "https://github.com",
    status: "เสร็จสิ้น",
    year: "2024",
    icon: "mdi:check-circle",
    color: "from-purple-500 to-pink-500",
    bgColor: "from-purple-50 to-pink-50 dark:from-purple-900/20 dark:to-pink-900/20",
    borderColor: "border-purple-200 dark:border-purple-700"
  },
  {
    id: 5,
    title: "Blog Platform",
    description: "แพลตฟอร์มบล็อกที่มีระบบจัดการเนื้อหา ระบบคอมเมนต์ และการค้นหา",
    image: 'https://images.unsplash.com/photo-1486312338219-ce68d2c6f44d?w=600&h=400&fit=crop',
    tags: ['Vue.js', 'Tailwind CSS', 'CMS', 'Search'],
    liveLink: 'https://example.com',
    codeLink: "https://github.com",
    status: "กำลังพัฒนา",
    year: "2024",
    icon: "mdi:blog",
    color: "from-indigo-500 to-purple-500",
    bgColor: "from-indigo-50 to-purple-50 dark:from-indigo-900/20 dark:to-purple-900/20",
    borderColor: "border-indigo-200 dark:border-indigo-700"
  },
  {
    id: 6,
    title: "Social Media App",
    description: "แอปพลิเคชันโซเชียลมีเดียที่มีระบบแชร์รูปภาพ คอมเมนต์ และติดตามเพื่อน",
    image: 'https://images.unsplash.com/photo-1611605698335-8b1569810432?w=600&h=400&fit=crop',
    tags: ['Vue.js', 'Tailwind CSS', 'Real-time', 'Upload'],
    liveLink: 'https://example.com',
    codeLink: "https://github.com",
    status: "วางแผน",
    year: "2025",
    icon: "mdi:share-variant",
    color: "from-pink-500 to-rose-500",
    bgColor: "from-pink-50 to-rose-50 dark:from-pink-900/20 dark:to-rose-900/20",
    borderColor: "border-pink-200 dark:border-pink-700"
  }
]);

// Reactive state
const projectsSection = ref(null);
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

  if (projectsSection.value) {
    observer.observe(projectsSection.value);
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
    ref="projectsSection"
    class="relative py-20 px-4 overflow-hidden"
    id="projects"
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
          <div class="w-32 h-32 bg-gradient-to-r from-purple-500/10 to-pink-500/10 rounded-full blur-3xl"></div>
        </div>
        
        <!-- Main Content -->
        <div class="relative z-10">
          <!-- Badge -->
          <div class="inline-flex items-center px-6 py-3 rounded-full bg-gradient-to-r from-purple-100 to-pink-100 dark:from-purple-900/30 dark:to-pink-900/30 border border-purple-200 dark:border-purple-700 mb-6">
            <Icon icon="mdi:folder-multiple" class="text-xl text-purple-600 dark:text-purple-400 mr-2" />
            <span class="text-sm font-semibold text-purple-700 dark:text-purple-300">ผลงานของผม</span>
          </div>
          
          <!-- Main Title -->
          <h2 class="text-5xl md:text-6xl lg:text-7xl font-black mb-6">
            <span class="bg-gradient-to-r from-purple-600 via-pink-600 to-orange-600 bg-clip-text text-transparent">
              โปรเจกต์ของผม
            </span>
          </h2>
          
          <!-- Subtitle -->
          <div class="flex items-center justify-center space-x-4 mb-6">
            <div class="w-12 h-0.5 bg-gradient-to-r from-transparent to-purple-500 rounded-full"></div>
            <p class="text-xl md:text-2xl text-slate-600 dark:text-slate-300 font-medium">
              ผลงานที่สร้างสรรค์ด้วยใจ
            </p>
            <div class="w-12 h-0.5 bg-gradient-to-r from-pink-500 to-transparent rounded-full"></div>
          </div>
          
          <!-- Description -->
          <p class="text-lg text-slate-500 dark:text-slate-400 max-w-2xl mx-auto leading-relaxed">
            โปรเจกต์ต่างๆ ที่ผมได้สร้างขึ้นเพื่อแสดงทักษะและความสามารถในการพัฒนาเว็บแอปพลิเคชัน
          </p>
        </div>
        
        <!-- Bottom Decoration -->
        <div class="absolute -bottom-8 left-1/2 transform -translate-x-1/2 flex items-center space-x-3">
          <div class="w-2 h-2 bg-purple-400 rounded-full animate-pulse"></div>
          <div class="w-16 h-0.5 bg-gradient-to-r from-purple-400 via-pink-400 to-orange-400 rounded-full"></div>
          <div class="w-2 h-2 bg-pink-400 rounded-full animate-pulse" style="animation-delay: 0.5s"></div>
          <div class="w-16 h-0.5 bg-gradient-to-r from-pink-400 via-orange-400 to-yellow-400 rounded-full"></div>
          <div class="w-2 h-2 bg-orange-400 rounded-full animate-pulse" style="animation-delay: 1s"></div>
        </div>
      </div>

      <!-- Projects Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="project in projects"
          :key="project.id"
          class="group relative overflow-hidden"
          data-aos="fade-up"
          :data-aos-delay="project.id * 100"
        >
          <!-- Project Card -->
          <div class="relative bg-white/90 dark:bg-slate-800/90 backdrop-blur-sm rounded-3xl overflow-hidden border border-slate-200/60 dark:border-slate-700/60 shadow-lg hover:shadow-2xl transition-all duration-500 hover:scale-105">
            
            <!-- Background Gradient -->
            <div 
              :class="`absolute inset-0 bg-gradient-to-br ${project.bgColor} opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
            />
            
            <!-- Floating Elements -->
            <div class="absolute -top-2 -right-2 w-4 h-4 bg-purple-400/30 rounded-full group-hover:animate-ping" />
            <div class="absolute -bottom-2 -left-2 w-3 h-3 bg-pink-400/30 rounded-full group-hover:animate-ping" style="animation-delay: 0.5s" />
            
            <!-- Image Container -->
            <div class="relative overflow-hidden">
              <img 
                :src="project.image" 
                :alt="project.title"
                class="w-full h-48 object-cover transition-transform duration-500 group-hover:scale-110"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500" />
              
              <!-- Status Badge -->
              <div class="absolute top-4 right-4">
                <span 
                  :class="`px-3 py-1 rounded-full text-xs font-semibold bg-gradient-to-r ${project.color} text-white shadow-lg`"
                >
                  {{ project.status }}
                </span>
              </div>
              
              <!-- Year Badge -->
              <div class="absolute top-4 left-4">
                <span class="px-3 py-1 rounded-full text-xs font-semibold bg-white/90 dark:bg-slate-800/90 text-slate-700 dark:text-slate-300 shadow-lg">
                  {{ project.year }}
                </span>
              </div>
            </div>

            <!-- Content -->
            <div class="relative z-10 p-6">
              <!-- Header -->
              <div class="flex items-start justify-between mb-4">
                <div class="flex items-center space-x-3">
                  <!-- Icon -->
                  <div 
                    :class="`w-12 h-12 rounded-xl bg-gradient-to-br ${project.color} flex items-center justify-center shadow-lg group-hover:scale-110 group-hover:rotate-3 transition-all duration-500`"
                  >
                    <Icon 
                      :icon="project.icon" 
                      class="text-xl text-white group-hover:animate-bounce" 
                    />
                  </div>
                  
                  <!-- Title -->
                  <div>
                    <h3 class="text-lg font-bold text-slate-800 dark:text-white group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-purple-600 group-hover:to-pink-600 group-hover:bg-clip-text transition-all duration-500">
                      {{ project.title }}
                    </h3>
                  </div>
                </div>
              </div>
              
              <!-- Description -->
              <p class="text-slate-600 dark:text-slate-300 text-sm leading-relaxed mb-4">
                {{ project.description }}
              </p>
              
              <!-- Tags -->
              <div class="flex flex-wrap gap-2 mb-4">
                <span 
                  v-for="(tag, index) in project.tags" 
                  :key="index"
                  class="px-2 py-1 rounded-full text-xs font-medium bg-slate-100 dark:bg-slate-700 text-slate-600 dark:text-slate-300"
                >
                  {{ tag }}
                </span>
              </div>
              
              <!-- Links -->
              <div class="flex items-center justify-between">
                <a 
                  :href="project.liveLink" 
                  target="_blank"
                  class="flex items-center space-x-2 text-purple-600 dark:text-purple-400 hover:text-purple-700 dark:hover:text-purple-300 transition-colors duration-300"
                >
                  <Icon icon="mdi:open-in-new" class="text-sm" />
                  <span class="text-sm font-medium">Live Demo</span>
                </a>
                <a 
                  :href="project.codeLink" 
                  target="_blank"
                  class="flex items-center space-x-2 text-pink-600 dark:text-pink-400 hover:text-pink-700 dark:hover:text-pink-300 transition-colors duration-300"
                >
                  <Icon icon="mdi:github" class="text-sm" />
                  <span class="text-sm font-medium">Source Code</span>
                </a>
              </div>
            </div>

            <!-- Bottom Accent -->
            <div 
              :class="`absolute bottom-0 left-0 right-0 h-1 bg-gradient-to-r ${project.color} opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Custom animations */
@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

.animate-float {
  animation: float 3s ease-in-out infinite;
}

/* Hover effects */
.group:hover .group-hover\:animate-float {
  animation: float 1s ease-in-out infinite;
}
</style>