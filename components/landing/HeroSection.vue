<template>
  <section class="relative min-h-[100dvh] flex flex-col lg:flex-row items-center overflow-hidden bg-black text-white py-16 md:py-24 lg:py-0">
    <!-- Background Gradient -->
    <div class="absolute top-0 left-0 w-full h-full overflow-hidden pointer-events-none">
      <div class="absolute top-[-10%] left-[-10%] w-[60%] h-[60%] bg-purple-900/20 rounded-full blur-[80px] md:blur-[120px]"></div>
      <div class="absolute bottom-[-10%] right-[-10%] w-[60%] h-[60%] bg-purple-900/10 rounded-full blur-[80px] md:blur-[120px]"></div>
      <div class="absolute top-[20%] left-[20%] w-[40%] h-[40%] bg-indigo-900/20 rounded-full blur-[60px] md:blur-[100px]"></div>
    </div>

    <div class="container mx-auto px-4 sm:px-6 lg:px-8 relative z-10 w-full flex-grow flex flex-col justify-center">
      <div class="grid lg:grid-cols-2 gap-12 lg:gap-20 items-center">
        <!-- Left Content -->
        <div class="space-y-6 md:space-y-8 animate-slide-up text-center lg:text-left pt-12 lg:pt-0">
          <!-- Badge -->
          <div class="flex justify-center lg:justify-start">
            <div class="inline-flex items-center gap-2 px-3 py-1.5 md:px-4 rounded-full bg-white/5 border border-white/10 backdrop-blur-sm transition-all hover:bg-white/10 cursor-default">
              <span class="px-1.5 py-0.5 rounded bg-primary-600 text-[11px] md:text-xs font-bold text-white tracking-wider">NEW</span>
              <span class="text-xs md:text-sm text-gray-300">BuidAI 应用市场上线，探索无限可能</span>
            </div>
          </div>

        <!-- Headline -->
        <div class="space-y-4 md:space-y-6 lg:space-y-8">
          <p class="text-sm sm:text-base lg:text-lg text-white/60 leading-relaxed tracking-wide">
            面向 <span class="text-white font-semibold">AI开发者</span> · <span class="text-white font-semibold">AI创业者</span> · <span class="text-white font-semibold">先进组织</span> 打造的
          </p>
          <h1 class="text-2xl sm:text-3xl lg:text-4xl xl:text-5xl font-semibold leading-tight tracking-tight text-white">
            <span class="relative inline-block underline decoration-wavy decoration-2 decoration-white/40 underline-offset-8">
              <span class="text-[#6A28F9]">企业级开源智能体</span> 搭建平台
            </span>
          </h1>
          <p class="text-base sm:text-lg lg:text-xl text-gray-400 max-w-2xl mx-auto lg:mx-0 leading-relaxed">
            它 <span class="text-white font-medium">正在</span> 努力成为AI应用落地的首选方案
          </p>
        </div>

          <!-- Buttons -->
          <div class="flex flex-col sm:flex-row justify-center lg:justify-start gap-4 pt-2 md:pt-4">
            <button class="w-full sm:w-auto px-8 py-3.5 rounded-full bg-gradient-to-r from-primary-600 to-primary-500 text-white font-medium text-lg hover:shadow-lg hover:shadow-primary-500/25 transition-all duration-300 transform hover:-translate-y-0.5 active:scale-95">
              开源部署
            </button>
            <button class="w-full sm:w-auto px-8 py-3.5 rounded-full bg-white text-gray-900 font-medium text-lg hover:bg-gray-100 transition-all duration-300 transform hover:-translate-y-0.5 active:scale-95">
              查看 Demo
            </button>
          </div>

          <!-- Feature Grid -->
          <div class="flex flex-wrap justify-center lg:justify-start gap-x-4 md:gap-x-8 gap-y-3 md:gap-y-4 pt-6 md:pt-8 text-xs sm:text-sm text-gray-400">
            <div class="flex items-center gap-1.5 md:gap-2">
              <svg class="w-4 h-4 text-purple-400 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>
              <span>AI原生内核</span>
            </div>
            <div class="flex items-center gap-1.5 md:gap-2">
              <svg class="w-4 h-4 text-purple-400 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z"/></svg>
              <span>组织管理</span>
            </div>
            <div class="flex items-center gap-1.5 md:gap-2">
              <svg class="w-4 h-4 text-purple-400 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"/></svg>
              <span>二次开发</span>
            </div>
            <div class="flex items-center gap-1.5 md:gap-2">
              <svg class="w-4 h-4 text-purple-400 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>
              <span>自定义LOGO</span>
            </div>
            <div class="flex items-center gap-1.5 md:gap-2">
              <svg class="w-4 h-4 text-purple-400 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.828 14.828a4 4 0 01-5.656 0M9 10h.01M15 10h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
              <span>简单易用</span>
            </div>
            <div class="flex items-center gap-1.5 md:gap-2">
              <svg class="w-4 h-4 text-purple-400 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"/></svg>
              <span>插件扩展无限可能</span>
            </div>
            <div class="flex items-center gap-1.5 md:gap-2">
              <svg class="w-4 h-4 text-purple-400 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"/></svg>
              <span>开源所有代码</span>
            </div>
          </div>
        </div>

        <!-- Spacer for Layout (Desktop only) -->
        <div class="hidden lg:block"></div>
      </div>
    </div>

    <!-- 右侧图片展示区 -->
    <div class="relative w-full lg:absolute lg:inset-y-0 lg:right-0 lg:w-1/2 flex items-end lg:items-center justify-center lg:justify-end z-10 animate-slide-up animation-delay-200 mt-12 lg:mt-0 pointer-events-none px-4 lg:px-0 pb-12 lg:pb-0">
       <!-- Layered Design Container -->
       <div class="relative w-full max-w-[500px] lg:max-w-[800px] perspective-1000 flex justify-center lg:justify-end pointer-events-auto">

         <!-- 背景层（偏移+半透明+旋转） -->
         <div class="absolute inset-0 w-full h-full opacity-60 transform scale-95 -rotate-3 -translate-x-4 translate-y-4 -z-10 transition-transform duration-700" :class="{ '-translate-x-8 translate-y-8 -rotate-6': !isMobile }">
           <img
             src="/home-bg.png"
             alt="BuidAI Dashboard Background"
             class="w-full h-auto object-contain rounded-lg"
           />
         </div>

         <!-- 主视觉层 -->
         <img
           src="/home-right-bg.png"
           alt="BuidAI Dashboard Interface"
           fetchpriority="high"
           class="relative w-full h-auto object-contain transform transition-transform duration-700 rounded-lg z-10"
           :class="{ 'hover:scale-[1.02]': !isMobile }"
         />

         <!-- 主视觉层（添加高斯模糊） -->
         <div class="absolute inset-0 bg-primary-500/20 blur-[60px] md:blur-[80px] -z-20 rounded-full"></div>
       </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

/**
 * Hero Section Logic
 * 包含响应式状态检测，用于优化移动端体验（如禁用复杂的悬停效果）
 */

// 响应式状态
const isMobile = ref(false)

// 检测设备类型
const checkDevice = () => {
  if (typeof window !== 'undefined') {
    isMobile.value = window.innerWidth < 768
  }
}

onMounted(() => {
  checkDevice()
  window.addEventListener('resize', checkDevice)
})

onUnmounted(() => {
  window.removeEventListener('resize', checkDevice)
})
</script>

<style scoped>
.perspective-1000 {
  perspective: 1000px;
}
</style>
