<script setup>
import { ref, onMounted } from 'vue'

// Social media links
const socialLinks = ref([
  {
    name: 'GitHub',
    icon: 'mdi:github',
    url: 'https://github.com/ixNcnlcc',
    color: 'hover:text-gray-400'
  },
  {
    name: 'Facebook',
    icon: 'mdi:facebook',
    url: 'https://www.facebook.com/NCNnutcha',
    color: 'hover:text-blue-400'
  },
  {
    name: 'Instagram',
    icon: 'mdi:instagram',
    url: 'https://www.instagram.com/ncnlc_?igsh=cndjczllMGxhc3Qw&utm_source=qr',
    color: 'hover:text-pink-400'
  },
  {
    name: 'Twitter',
    icon: 'mdi:twitter',
    url: 'https://x.com/ixncnlc?s=11',
    color: 'hover:text-blue-300'
  },
])

// Quick links
const quickLinks = ref([
  { name: 'หน้าแรก', href: '#top' },
  { name: 'เกี่ยวกับฉัน', href: '#why-me' },
  { name: 'ทักษะ', href: '#skills' },
  { name: 'บริการ', href: '#services' },
  { name: 'โปรเจกต์', href: '#projects' },
  { name: 'ติดต่อ', href: '#contact' }
])

// Contact info
const contactInfo = ref({
  email: 'nutchanonac97@gmail.com',
  phone: '+66 93-387-7341',
  location: 'กรุงเทพมหานคร, ประเทศไทย',
  birthDate: '20/05/1997',
  position: 'ตำแหน่ง นักศึกษาฝึกงาน'
})

// Current year
const currentYear = ref(new Date().getFullYear())

// Name toggle between Thai and English
const showThaiName = ref(true)
const toggleName = () => {
  showThaiName.value = !showThaiName.value
}

// Personal info
const personalInfo = ref({
  thaiName: 'นัชชานนท์ เอ้งฉ้วน',
  englishName: 'Nutchanon Angchoun',
  description: 'นักพัฒนาซอฟต์แวร์ที่มีความสนใจในการสร้างแอปพลิเคชันเว็บที่ใช้งานได้จริงและมีดีไซน์สวยงาม เชี่ยวชาญในการใช้ Vue.js, React และ Node.js ในการพัฒนา พร้อมเรียนรู้เทคโนโลยีใหม่ๆ และร่วมงานในโปรเจกต์ที่น่าสนใจ'
})

// Scroll to top function
const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

// Show scroll to top button
const showScrollTop = ref(false)

onMounted(() => {
  const handleScroll = () => {
    showScrollTop.value = window.scrollY > 300
  }
  
  window.addEventListener('scroll', handleScroll)
  
  return () => {
    window.removeEventListener('scroll', handleScroll)
  }
})
</script>

<template>
  <footer class="bg-slate-900 text-white">
    <div class="container mx-auto px-4 py-12">
      <!-- Main Content -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-8">
        <!-- Brand Section -->
        <div class="text-center md:text-left">
          <h3 
            @click="toggleName"
            class="text-2xl font-bold text-white mb-2 cursor-pointer hover:text-blue-400 transition-colors duration-300"
            :title="showThaiName ? 'คลิกเพื่อเปลี่ยนเป็นภาษาอังกฤษ' : 'Click to switch to Thai'"
          >
            {{ showThaiName ? personalInfo.thaiName : personalInfo.englishName }}
          </h3>
          <p class="text-gray-400 text-sm mb-4">{{ contactInfo.position }}</p>
          <p class="text-gray-300 text-sm leading-relaxed mb-6">
            {{ personalInfo.description }}
          </p>
          
          <!-- Social Links -->
          <div class="flex justify-center md:justify-start space-x-3">
            <a 
              v-for="social in socialLinks" 
              :key="social.name"
              :href="social.url"
              :aria-label="social.name"
              class="w-10 h-10 bg-slate-800 rounded-lg flex items-center justify-center hover:bg-blue-600 transition-colors duration-300"
              target="_blank"
              rel="noopener noreferrer"
            >
              <Icon 
                :icon="social.icon" 
                class="w-5 h-5 text-gray-300 hover:text-white"
              />
            </a>
          </div>
        </div>

        <!-- Quick Links -->
        <div class="text-center md:text-left">
          <h4 class="text-lg font-semibold text-white mb-4">ลิงก์ด่วน</h4>
          <div class="grid grid-cols-2 gap-x-4 gap-y-2">
            <div v-for="link in quickLinks" :key="link.name">
              <a 
                :href="link.href"
                class="text-gray-400 hover:text-white transition-colors duration-300 text-sm flex items-center group"
              >
                <Icon icon="mdi:chevron-right" class="w-3 h-3 mr-1 group-hover:translate-x-1 transition-transform duration-300" />
                {{ link.name }}
              </a>
            </div>
          </div>
        </div>

        <!-- Contact Info -->
        <div class="text-center md:text-left">
          <h4 class="text-lg font-semibold text-white mb-4">ติดต่อ</h4>
          <div class="space-y-3">
            <div class="flex items-center justify-center md:justify-start text-gray-400 text-sm">
              <Icon icon="mdi:email" class="w-4 h-4 mr-2 text-blue-400" />
              <a :href="`mailto:${contactInfo.email}`" class="hover:text-white transition-colors duration-300">
                {{ contactInfo.email }}
              </a>
            </div>
            <div class="flex items-center justify-center md:justify-start text-gray-400 text-sm">
              <Icon icon="mdi:phone" class="w-4 h-4 mr-2 text-green-400" />
              <a :href="`tel:${contactInfo.phone}`" class="hover:text-white transition-colors duration-300">
                {{ contactInfo.phone }}
              </a>
            </div>
            <div class="flex items-center justify-center md:justify-start text-gray-400 text-sm">
              <Icon icon="mdi:map-marker" class="w-4 h-4 mr-2 text-red-400" />
              <span>{{ contactInfo.location }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Divider -->
      <div class="border-t border-slate-700 my-6"></div>

      <!-- Bottom Section -->
      <div class="flex flex-col md:flex-row justify-between items-center">
        <div class="text-center md:text-left mb-4 md:mb-0">
          <p class="text-gray-400 text-sm">
            &copy; {{ currentYear }} {{ showThaiName ? personalInfo.thaiName : personalInfo.englishName }}. สงวนลิขสิทธิ์ทั้งหมด
          </p>
        </div>
        
        <div class="flex items-center space-x-6 text-sm text-gray-400">
          <a href="#" class="hover:text-white transition-colors duration-300">นโยบายความเป็นส่วนตัว</a>
          <a href="#" class="hover:text-white transition-colors duration-300">เงื่อนไขการใช้งาน</a>
          <a href="#" class="hover:text-white transition-colors duration-300">คุกกี้</a>
        </div>
      </div>
    </div>

    <!-- Scroll to Top Button -->
    <Transition
      enter-active-class="transition-all duration-300 ease-out"
      enter-from-class="opacity-0 scale-75 translate-y-4"
      enter-to-class="opacity-100 scale-100 translate-y-0"
      leave-active-class="transition-all duration-300 ease-in"
      leave-from-class="opacity-100 scale-100 translate-y-0"
      leave-to-class="opacity-0 scale-75 translate-y-4"
    >
      <button
        v-if="showScrollTop"
        @click="scrollToTop"
        class="fixed bottom-8 right-8 w-12 h-12 bg-gradient-to-r from-blue-500 to-purple-500 hover:from-blue-600 hover:to-purple-600 rounded-full flex items-center justify-center shadow-lg hover:shadow-xl transition-all duration-300 hover:scale-110 z-50 group"
        aria-label="กลับขึ้นด้านบน"
      >
        <Icon 
          icon="mdi:chevron-up" 
          class="w-6 h-6 text-white group-hover:animate-bounce"
        />
      </button>
    </Transition>
  </footer>
</template>

<style scoped>
/* Custom animations */
@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

.animate-float {
  animation: float 6s ease-in-out infinite;
}

/* Hover effects for links */
.group:hover .group-hover\:translate-x-1 {
  transform: translateX(0.25rem);
}
</style>