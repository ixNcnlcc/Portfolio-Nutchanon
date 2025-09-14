<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import SectionHeader from "@/components/UI/SectionHeader.vue";
import Button from "@/components/UI/Button.vue";

// Constants
const OBSERVER_THRESHOLD = 0.3;

const formData = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
});

const contactInfo = ref([
  {
    id: 1,
    icon: 'mdi:email',
    title: 'Email',
    value: 'nutchanonac97@gmail.com',
    link: 'mailto:nutchanonac97@gmail.com',
    color: "from-blue-500 to-cyan-500",
    bgColor: "from-blue-50 to-cyan-50 dark:from-blue-900/20 dark:to-cyan-900/20",
    borderColor: "border-blue-200 dark:border-blue-700"
  },
  {
    id: 2,
    icon: 'mdi:phone',
    title: 'Phone',
    value: '+66 93-387-7341',
    link: 'tel:+66933877341',
    color: "from-green-500 to-emerald-500",
    bgColor: "from-green-50 to-emerald-50 dark:from-green-900/20 dark:to-green-900/20",
    borderColor: "border-green-200 dark:border-green-700"
  },
  {
    id: 3,
    icon: 'mdi:map-marker',
    title: 'Location',
    value: 'กรุงเทพมหานคร, ประเทศไทย',
    link: '#',
    color: "from-purple-500 to-pink-500",
    bgColor: "from-purple-50 to-pink-50 dark:from-purple-900/20 dark:to-pink-900/20",
    borderColor: "border-purple-200 dark:border-purple-700"
  },
  
]);

const socialLinks = ref([
  {
    id: 1,
    name: 'GitHub',
    icon: 'mdi:github',
    url: 'https://github.com/ixNcnlcc',
    color: "from-gray-500 to-slate-500",
    bgColor: "from-gray-50 to-slate-50 dark:from-gray-900/20 dark:to-slate-900/20",
    borderColor: "border-gray-200 dark:border-gray-700"
  },
  {
    id: 2,
    name: 'Facebook',
    icon: 'mdi:facebook',
    url: 'https://www.facebook.com/NCNnutcha',
    color: "from-pink-500 to-rose-500",
    bgColor: "from-pink-50 to-rose-50 dark:from-pink-900/20 dark:to-rose-900/20",
    borderColor: "border-pink-200 dark:border-pink-700"
  },
  {
    id: 3,
    name: 'Instagram',
    icon: 'mdi:instagram',
    url: 'https://www.instagram.com/ncnlc_?igsh=cndjczllMGxhc3Qw&utm_source=qr',
    color: "from-gray-500 to-slate-500",
    bgColor: "from-gray-50 to-slate-50 dark:from-gray-900/20 dark:to-slate-900/20",
    borderColor: "border-gray-200 dark:border-gray-700"
  },
  {
    id: 4,
    name: 'Twitter',
    icon: 'mdi:twitter',
    url: 'https://x.com/ixncnlc?s=11',
    color: "from-blue-600 to-blue-700",
    bgColor: "from-blue-50 to-blue-100 dark:from-blue-900/20 dark:to-blue-800/20",
    borderColor: "border-blue-200 dark:border-blue-700"
  }
]);

// Reactive state
const contactSection = ref(null);
const isVisible = ref(false);

// Methods
const handleSubmit = () => {
  console.log('Form submitted:', formData.value);
  // Handle form submission here
};

// Intersection Observer
const observer = ref(null);

onMounted(() => {
  observer.value = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          isVisible.value = true;
        }
      });
    },
    { threshold: OBSERVER_THRESHOLD }
  );

  if (contactSection.value) {
    observer.value.observe(contactSection.value);
  }
});

onUnmounted(() => {
  if (observer.value) {
    observer.value.disconnect();
  }
});
</script>

<template>
  <section 
    id="contact" 
    ref="contactSection"
    class="relative py-16 lg:py-24"
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

    <!-- Main Content -->
    <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Badge -->
      <div class="flex justify-center mb-6">
        <div class="inline-flex items-center px-6 py-3 rounded-full bg-gradient-to-r from-blue-500/10 to-purple-500/10 dark:from-blue-400/20 dark:to-purple-400/20 border border-blue-200/50 dark:border-blue-400/30">
          <Icon icon="mdi:email" class="text-xl text-blue-600 dark:text-blue-400 mr-2" />
          <span class="text-sm font-semibold text-blue-700 dark:text-blue-300">ติดต่อผม</span>
        </div>
      </div>

      <!-- Main Title -->
      <h2 class="text-5xl md:text-6xl lg:text-7xl font-black mb-6 text-center">
        <span class="bg-gradient-to-r from-blue-600 via-purple-600 to-pink-600 bg-clip-text text-transparent">
          ติดต่อ
        </span>
      </h2>

      <!-- Subtitle -->
      <div class="flex items-center justify-center space-x-4 mb-6">
        <div class="w-12 h-0.5 bg-gradient-to-r from-transparent to-blue-500 rounded-full"></div>
        <p class="text-xl md:text-2xl text-gray-700 dark:text-gray-200 font-medium">
          พร้อมที่จะทำงานร่วมกัน
        </p>
        <div class="w-12 h-0.5 bg-gradient-to-r from-purple-500 to-transparent rounded-full"></div>
      </div>

      <!-- Description -->
      <p class="text-lg text-gray-600 dark:text-gray-300 max-w-2xl mx-auto leading-relaxed mb-16 text-center">
        ผมพร้อมที่จะรับฟังไอเดียและความต้องการของคุณ ไม่ว่าจะเป็นโปรเจกต์เล็กหรือใหญ่ ผมพร้อมที่จะช่วยทำให้เป็นจริง
      </p>

      <!-- Contact Content -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-start">
        
        <!-- Left Column - Contact Information -->
        <div class="space-y-8 order-2 lg:order-1">
          <!-- Contact Cards -->
          <div class="space-y-6">
            <div 
              v-for="contact in contactInfo" 
              :key="contact.id"
              class="group p-6 rounded-2xl border border-gray-200 dark:border-gray-700 bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm transition-all duration-300 transform hover:scale-105 hover:shadow-xl hover:border-blue-300 dark:hover:border-blue-500"
              data-aos="fade-up"
              :data-aos-delay="contact.id * 100"
            >
              <div class="flex items-center space-x-4">
                <div 
                  :class="[
                    'w-16 h-16 rounded-2xl flex items-center justify-center shadow-lg group-hover:shadow-xl transition-all duration-300 relative overflow-hidden group',
                    contact.color
                  ]"
                >
                  <div class="absolute inset-0 bg-black/10 dark:bg-transparent group-hover:bg-transparent dark:group-hover:bg-white/10 transition-all duration-300"></div>
                  <Icon 
                    :icon="contact.icon" 
                    :class="[
                      'text-2xl drop-shadow-lg relative z-10 filter brightness-110 contrast-125 group-hover:brightness-125 group-hover:contrast-150 dark:group-hover:brightness-150 dark:group-hover:contrast-200 transition-all duration-300',
                      contact.id === 1 ? 'text-blue-600 dark:text-white group-hover:text-blue-500 dark:group-hover:text-blue-200' : '',
                      contact.id === 2 ? 'text-green-600 dark:text-white group-hover:text-green-500 dark:group-hover:text-green-200' : '',
                      contact.id === 3 ? 'text-purple-600 dark:text-white group-hover:text-purple-500 dark:group-hover:text-purple-200' : '',
                      contact.id === 4 ? 'text-pink-600 dark:text-white group-hover:text-pink-500 dark:group-hover:text-pink-200' : '',
                      contact.id === 5 ? 'text-indigo-600 dark:text-white group-hover:text-indigo-500 dark:group-hover:text-indigo-200' : ''
                    ]"
                    style="text-shadow: 0 2px 4px rgba(0,0,0,0.9);" 
                  />
                </div>
                <div class="flex-1">
                  <h4 class="text-lg font-bold text-gray-900 dark:text-white mb-1">
                    {{ contact.title }}
                  </h4>
                  <a 
                    :href="contact.link" 
                    class="text-gray-600 dark:text-gray-300 hover:text-blue-600 dark:hover:text-blue-400 transition-colors duration-300 font-medium"
                  >
                    {{ contact.value }}
                  </a>
                </div>
              </div>
            </div>
          </div>

          <!-- Social Media -->
          <div 
            class="text-center lg:text-left"
            data-aos="fade-up"
            data-aos-delay="400"
          >
            <h4 class="text-xl font-bold text-gray-900 dark:text-white mb-6">
              ติดตามผมได้ที่
            </h4>
            <div class="flex justify-center lg:justify-start space-x-4">
              <a 
                v-for="social in socialLinks" 
                :key="social.id"
                :href="social.url" 
                target="_blank"
                class="w-14 h-14 rounded-2xl flex items-center justify-center border border-gray-200 dark:border-gray-700 bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm transition-all duration-300 transform hover:scale-110 hover:shadow-lg hover:border-blue-300 dark:hover:border-blue-500 group"
                :title="social.name"
              >
                <Icon 
                  :icon="social.icon" 
                  :class="[
                    'text-2xl text-gray-600 dark:text-gray-400 transition-all duration-300 group-hover:scale-110',
                    social.name === 'GitHub' ? 'group-hover:text-gray-800 dark:group-hover:text-gray-200' : '',
                    social.name === 'Facebook' ? 'group-hover:text-blue-600 dark:group-hover:text-blue-300' : '',
                    social.name === 'Instagram' ? 'group-hover:text-pink-600 dark:group-hover:text-pink-300' : '',
                    social.name === 'Twitter' ? 'group-hover:text-blue-500 dark:group-hover:text-blue-300' : ''
                  ]"
                />
                </a>
            </div>
          </div>
        </div>

        <!-- Right Column - Contact Form -->
        <div 
          class="bg-white/90 dark:bg-gray-800/90 backdrop-blur-sm rounded-3xl shadow-2xl p-8 border border-gray-200 dark:border-gray-700 order-1 lg:order-2"
          data-aos="fade-left"
          data-aos-delay="200"
        >
          <div class="text-center mb-8">
            <h3 class="text-2xl md:text-3xl font-bold text-gray-900 dark:text-white mb-4">
              ส่งข้อความถึงผม
            </h3>
            <p class="text-gray-600 dark:text-gray-300">
              กรอกข้อมูลด้านล่าง และผมจะติดต่อกลับไปหาคุณ
            </p>
          </div>
          
          <form @submit.prevent="handleSubmit" class="space-y-6">
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
              <div>
                <label for="name" class="block text-sm font-bold text-gray-700 dark:text-gray-300 mb-2">
                  ชื่อ-นามสกุล
                </label>
              <input
                id="name"
                v-model="formData.name"
                type="text"
                required
                class="w-full px-4 py-3 border-2 border-gray-300 dark:border-gray-600 rounded-xl focus:ring-2 focus:ring-blue-500 focus:border-blue-500 bg-white/90 dark:bg-gray-700/90 backdrop-blur-sm text-gray-900 dark:text-white transition-all duration-300 placeholder-gray-500 shadow-sm"
                placeholder="ชื่อของคุณ"
              />
              </div>
              <div>
                <label for="email" class="block text-sm font-bold text-gray-700 dark:text-gray-300 mb-2">
                  อีเมล
                </label>
              <input
                id="email"
                v-model="formData.email"
                type="email"
                required
                class="w-full px-4 py-3 border-2 border-gray-300 dark:border-gray-600 rounded-xl focus:ring-2 focus:ring-blue-500 focus:border-blue-500 bg-white/90 dark:bg-gray-700/90 backdrop-blur-sm text-gray-900 dark:text-white transition-all duration-300 placeholder-gray-500 shadow-sm"
                placeholder="your@email.com"
              />
              </div>
            </div>
            
            <div>
              <label for="subject" class="block text-sm font-bold text-gray-700 dark:text-gray-300 mb-2">
                หัวข้อ
              </label>
              <input
                id="subject"
                v-model="formData.subject"
                type="text"
                required
                class="w-full px-4 py-3 border-2 border-gray-300 dark:border-gray-600 rounded-xl focus:ring-2 focus:ring-blue-500 focus:border-blue-500 bg-white/90 dark:bg-gray-700/90 backdrop-blur-sm text-gray-900 dark:text-white transition-all duration-300 placeholder-gray-500 shadow-sm"
                placeholder="หัวข้อที่ต้องการติดต่อ"
              />
            </div>
            
            <div>
              <label for="message" class="block text-sm font-bold text-gray-700 dark:text-gray-300 mb-2">
                ข้อความ
              </label>
              <textarea
                id="message"
                v-model="formData.message"
                rows="6"
                required
                class="w-full px-4 py-3 border-2 border-gray-300 dark:border-gray-600 rounded-xl focus:ring-2 focus:ring-blue-500 focus:border-blue-500 bg-white/90 dark:bg-gray-700/90 backdrop-blur-sm text-gray-900 dark:text-white transition-all duration-300 resize-none placeholder-gray-500 shadow-sm"
                placeholder="บอกผมเกี่ยวกับโปรเจกต์หรือความต้องการของคุณ..."
              ></textarea>
            </div>
            
            <div class="flex justify-center">
              <button
                type="submit"
                class="px-8 py-4 bg-gradient-to-r from-blue-600 to-purple-600 hover:from-blue-700 hover:to-purple-700 text-white rounded-xl font-bold text-lg transition-all duration-300 transform hover:scale-105 shadow-xl hover:shadow-2xl relative overflow-hidden group"
              >
                <span class="relative z-10">ส่งข้อความ</span>
                <div class="absolute inset-0 bg-gradient-to-r from-purple-500 to-pink-500 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
              </button>
        </div>
      </form>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
</style>