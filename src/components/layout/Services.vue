<script setup>
import { ref } from "vue";

// Services data
const services = ref([
  {
    id: 1,
    title: "Web Development",
    description: "สร้างเว็บไซต์ที่สวยงาม ใช้งานง่าย และมีประสิทธิภาพสูง ด้วยเทคโนโลยีล่าสุด",
    icon: "mdi:web",
    color: "from-blue-500 to-cyan-500",
    bgColor: "from-blue-50 to-cyan-50 dark:from-blue-900/20 dark:to-cyan-900/20",
    borderColor: "border-blue-200 dark:border-blue-700",
    features: ["Responsive Design", "Fast Loading", "SEO Optimized"]
  },
  {
    id: 2,
    title: "Mobile Development",
    description: "พัฒนาแอปพลิเคชันมือถือที่ทันสมัย ใช้งานง่าย และรองรับทุกแพลตฟอร์ม",
    icon: "mdi:cellphone",
    color: "from-purple-500 to-pink-500",
    bgColor: "from-purple-50 to-pink-50 dark:from-purple-900/20 dark:to-pink-900/20",
    borderColor: "border-purple-200 dark:border-purple-700",
    features: ["Cross Platform", "Native Performance", "User Friendly"]
  },
  {
    id: 3,
    title: "UI/UX Design",
    description: "ออกแบบอินเทอร์เฟซที่สวยงาม ใช้งานง่าย และสร้างประสบการณ์ที่ดีให้ผู้ใช้",
    icon: "mdi:palette",
    color: "from-green-500 to-emerald-500",
    bgColor: "from-green-50 to-emerald-50 dark:from-green-900/20 dark:to-emerald-900/20",
    borderColor: "border-green-200 dark:border-green-700",
    features: ["Modern Design", "User Experience", "Accessibility"]
  },
  {
    id: 4,
    title: "Database Design",
    description: "ออกแบบและจัดการฐานข้อมูลที่มีประสิทธิภาพ ปลอดภัย และขยายได้",
    icon: "mdi:database",
    color: "from-orange-500 to-red-500",
    bgColor: "from-orange-50 to-red-50 dark:from-orange-900/20 dark:to-red-900/20",
    borderColor: "border-orange-200 dark:border-orange-700",
    features: ["Data Security", "High Performance", "Scalable"]
  },
  {
    id: 5,
    title: "API Development",
    description: "สร้าง API ที่มีประสิทธิภาพ ปลอดภัย และง่ายต่อการใช้งาน",
    icon: "mdi:api",
    color: "from-indigo-500 to-purple-500",
    bgColor: "from-indigo-50 to-purple-50 dark:from-indigo-900/20 dark:to-purple-900/20",
    borderColor: "border-indigo-200 dark:border-indigo-700",
    features: ["RESTful API", "Documentation", "Testing"]
  },
  {
    id: 6,
    title: "Cloud Solutions",
    description: "จัดการและปรับใช้แอปพลิเคชันบนคลาวด์อย่างมีประสิทธิภาพ",
    icon: "mdi:cloud",
    color: "from-teal-500 to-blue-500",
    bgColor: "from-teal-50 to-blue-50 dark:from-teal-900/20 dark:to-blue-900/20",
    borderColor: "border-teal-200 dark:border-teal-700",
    features: ["Scalable", "Cost Effective", "Reliable"]
  }
]);
</script>

<template>
  <section 
    id="services" 
    class="relative py-20 px-4 overflow-hidden"
  >
    <!-- Background Elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div
        class="absolute -top-40 -right-40 w-80 h-80 bg-gradient-to-br from-blue-400 to-purple-600 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-pulse"
        style="animation-duration: 6s;"
      />
      <div
        class="absolute -bottom-40 -left-40 w-80 h-80 bg-gradient-to-br from-pink-400 to-red-600 rounded-full mix-blend-multiply filter blur-xl opacity-20 animate-pulse"
        style="animation-duration: 8s; animation-delay: 2s;"
      />
      <div
        class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-96 h-96 bg-gradient-to-br from-yellow-400 to-orange-600 rounded-full mix-blend-multiply filter blur-xl opacity-10 animate-pulse"
        style="animation-duration: 10s; animation-delay: 4s;"
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
            <Icon icon="mdi:cog" class="text-xl text-blue-600 dark:text-blue-400 mr-2" />
            <span class="text-sm font-semibold text-blue-700 dark:text-blue-300">บริการของผม</span>
          </div>
          
          <!-- Main Title -->
          <h2 class="text-5xl md:text-6xl lg:text-7xl font-black mb-6">
            <span class="bg-gradient-to-r from-blue-600 via-purple-600 to-pink-600 bg-clip-text text-transparent">
              บริการที่ให้
            </span>
          </h2>
          
          <!-- Subtitle -->
          <div class="flex items-center justify-center space-x-4 mb-6">
            <div class="w-12 h-0.5 bg-gradient-to-r from-transparent to-blue-500 rounded-full"></div>
            <p class="text-xl md:text-2xl text-slate-600 dark:text-slate-300 font-medium">
              สิ่งที่ผมสามารถช่วยคุณได้
            </p>
            <div class="w-12 h-0.5 bg-gradient-to-r from-purple-500 to-transparent rounded-full"></div>
          </div>
          
          <!-- Description -->
          <p class="text-lg text-slate-500 dark:text-slate-400 max-w-2xl mx-auto leading-relaxed">
            บริการด้านเทคโนโลยีที่หลากหลาย เพื่อตอบสนองความต้องการของคุณอย่างครบครัน
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

      <!-- Services Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="service in services"
          :key="service.id"
          class="group relative overflow-hidden"
          data-aos="fade-up"
          :data-aos-delay="service.id * 100"
        >
          <!-- Service Card -->
          <div class="relative bg-white/90 dark:bg-slate-800/90 backdrop-blur-sm rounded-3xl p-8 text-center border border-slate-200/60 dark:border-slate-700/60 shadow-lg hover:shadow-2xl transition-all duration-500 hover:scale-105">
            
            <!-- Background Gradient -->
            <div 
              :class="`absolute inset-0 bg-gradient-to-br ${service.bgColor} opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
            />
            
            <!-- Floating Elements -->
            <div class="absolute -top-2 -right-2 w-4 h-4 bg-blue-400/30 rounded-full group-hover:animate-ping" />
            <div class="absolute -bottom-2 -left-2 w-3 h-3 bg-purple-400/30 rounded-full group-hover:animate-ping" style="animation-delay: 0.5s" />
            
            <!-- Icon Container -->
            <div class="relative z-10 mb-6">
              <div 
                :class="`w-20 h-20 mx-auto rounded-3xl bg-gradient-to-br ${service.color} flex items-center justify-center shadow-lg group-hover:scale-110 group-hover:rotate-3 transition-all duration-500`"
              >
                <Icon 
                  :icon="service.icon" 
                  class="text-3xl text-white group-hover:animate-bounce" 
                />
              </div>
              
              <!-- Icon Glow -->
              <div 
                :class="`absolute inset-0 w-20 h-20 mx-auto rounded-3xl bg-gradient-to-br ${service.color} opacity-0 group-hover:opacity-30 blur-xl transition-opacity duration-500`"
              />
            </div>

            <!-- Content -->
            <div class="relative z-10">
              <!-- Title -->
              <h3 class="text-xl font-bold text-slate-800 dark:text-white mb-4 group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-blue-600 group-hover:to-purple-600 group-hover:bg-clip-text transition-all duration-500">
                {{ service.title }}
              </h3>
              
              <!-- Description -->
              <p class="text-slate-600 dark:text-slate-300 mb-6 leading-relaxed">
                {{ service.description }}
              </p>
              
              <!-- Features -->
              <div class="space-y-2">
                <div 
                  v-for="feature in service.features"
                  :key="feature"
                  class="flex items-center justify-center space-x-2"
                >
                  <div 
                    :class="`w-2 h-2 rounded-full bg-gradient-to-r ${service.color}`"
                  />
                  <span class="text-sm text-slate-500 dark:text-slate-400 font-medium">
                    {{ feature }}
                  </span>
                </div>
              </div>
            </div>

            <!-- Bottom Accent -->
            <div 
              :class="`absolute bottom-0 left-1/2 transform -translate-x-1/2 w-12 h-1 bg-gradient-to-r ${service.color} rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-500`"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
