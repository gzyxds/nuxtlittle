<template>
  <section class="py-24 bg-black overflow-hidden relative">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8 mb-20 text-center">
      <h2 class="text-3xl md:text-5xl font-bold text-white mb-6 tracking-tight">
        BuidAI 可以帮你做什么
      </h2>
      <p class="text-gray-400 text-lg tracking-wide">
        部署 BuidAI 无限拓展应用场景
      </p>
    </div>

    <!-- 3D 轮播容器 -->
    <div class="relative w-full">
      <div
        class="flex gap-4 sm:gap-8 overflow-x-auto pb-20 pt-10 px-4 sm:px-[50vw] scrollbar-hide perspective-container select-none"
        :class="{ 'cursor-grab': !isDragging, 'cursor-grabbing': isDragging }"
        ref="scrollContainer"
        @scroll="handleScroll"
        @mousedown="startDrag"
        @mousemove="onDrag"
        @mouseup="stopDrag"
        @mouseleave="stopDrag"
        @touchstart="stopDrag"
      >
        <div
          v-for="(card, index) in cards"
          :key="index"
          class="flex-shrink-0 w-[85vw] sm:w-[360px] perspective-item will-change-transform"
          :ref="(el) => { if(el) cardRefs[index] = el as HTMLElement }"
        >
          <div
            class="group relative h-auto min-h-[400px] rounded-xl overflow-hidden transition-all duration-300 hover:shadow-2xl hover:scale-[1.02]"
            :class="`bg-gradient-to-b ${card.gradient}`"
          >

            <!-- Content -->
            <div class="p-8 h-full flex flex-col relative z-10">
              <h3 class="text-2xl font-bold text-gray-900 mb-4 transition-colors">
                {{ card.title }}
              </h3>
              <p class="text-gray-700 text-sm leading-relaxed mb-4 line-clamp-6 font-medium">
                {{ card.desc }}
              </p>

              <div class="mt-2 rounded-lg overflow-hidden h-40 relative shadow-inner flex-shrink-0">
                 <img
                   :src="card.image"
                   :alt="card.title"
                   class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-500 opacity-90 group-hover:opacity-100"
                   loading="lazy"
                   draggable="false"
                 />
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- 淡入边缘（暗） -->
      <div class="absolute inset-y-0 left-0 w-64 bg-gradient-to-r from-black via-black/80 to-transparent pointer-events-none z-10"></div>
      <div class="absolute inset-y-0 right-0 w-64 bg-gradient-to-l from-black via-black/80 to-transparent pointer-events-none z-10"></div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, nextTick } from 'vue'

const cards = [
  {
    title: 'Sora2短剧视频创作',
    desc: 'Sora2短剧视频创作是一款聚焦高效优质短剧创作的AI智能生成工具，它能深度理解用户输入的文字提示词，将创意转化为精彩视频。',
    image: '/plugin/Sora2短剧视频创作.png',
    gradient: 'from-[#E0F2FE] to-[#BAE6FD]' // Sky Blue
  },
  {
    title: 'Nanobanana',
    desc: '香蕉绘画预置多个模版，开箱即用。结合gemini-3-pro-image-preview的生图能力，能够有效保持角色一致性。',
    image: '/plugin/Nanobanana.png',
    gradient: 'from-[#F3E8FF] to-[#E9D5FF]' // Purple
  },
  {
    title: 'AI简历',
    desc: 'AI简历致力于高效生成与深度优化您的个人简历，帮助您节省时间的同时，显著提升简历质量与影响力。',
    image: '/plugin/AI简历.png',
    gradient: 'from-[#FFE4E6] to-[#FECDD3]' // Rose
  },
  {
    title: '思维导图',
    desc: '各种结构的思维导图，支持自由导图样式，修改前台显示名称，帮助您理清思路，激发创意。',
    image: '/plugin/思维导图.png',
    gradient: 'from-[#FEF3C7] to-[#FDE68A]' // Amber
  },
  {
    title: 'AI 证件照',
    desc: '各种证件照类型，尺寸自定义，生成图片导出。无需跑照相馆，在家即可轻松制作专业证件照。',
    image: '/plugin/AI 证件照.png',
    gradient: 'from-[#D1FAE5] to-[#A7F3D0]' // Emerald
  },
  {
    title: '智能写作助手',
    desc: '在线编辑，支持AI改写，自定义模板助手。无论是文案创作还是日常写作，都能助您一臂之力。',
    image: '/plugin/智能写作助手.png',
    gradient: 'from-[#E0E7FF] to-[#C7D2FE]' // Indigo
  },
  {
    title: 'AI PPT',
    desc: '智能生成PPT，一键排版，海量模板，让演示更出彩。告别繁琐的排版工作，专注于内容创作。',
    image: '/plugin/AI PPT.png',
    gradient: 'from-[#FFEDD5] to-[#FED7AA]' // Orange
  },
  {
    title: 'AI合同',
    desc: '智能合同审查与生成，降低法律风险，提高签约效率。专业的法律助手，为您的商业合作保驾护航。',
    image: '/plugin/AI合同.png',
    gradient: 'from-[#CCFBF1] to-[#99F6E4]' // Teal
  },
  {
    title: 'AI商图秀',
    desc: '电商主图智能生成，模特替换，场景合成，提升点击率。无需专业摄影，也能制作出高质量的商品展示图。',
    image: '/plugin/AI商图秀.png',
    gradient: 'from-[#FAE8FF] to-[#F5D0FE]' // Fuchsia
  },
  {
    title: 'AI直播短视频数字人',
    desc: '7x24小时无人直播，数字人带货，低成本高回报。打造永不休息的超级主播，抢占直播红利。',
    image: '/plugin/AI直播短视频数字人.png',
    gradient: 'from-[#ECFEFF] to-[#A5F3FC]' // Cyan
  },
  {
    title: 'AI短剧小说创作',
    desc: '辅助短剧剧本创作，小说续写，激发创作灵感。从灵感到剧本，AI全程陪伴，让创作变得简单有趣。',
    image: '/plugin/AI短剧小说创作.png',
    gradient: 'from-[#FEF9C3] to-[#FDE047]' // Yellow
  },
  {
    title: 'GEO优化排名工具',
    desc: '基于地理位置的SEO优化工具，提升本地搜索排名。精准锁定目标客户，让生意自动找上门。',
    image: '/plugin/GEO优化排名工具.png',
    gradient: 'from-[#FEE2E2] to-[#FECACA]' // Red
  },
  {
    title: '即梦AI绘画',
    desc: '文本生成图片，艺术创作，风格迁移，释放你的想象力。无论是二次元还是写实风，都能轻松驾驭。',
    image: '/plugin/即梦AI绘画.png',
    gradient: 'from-[#EDE9FE] to-[#DDD6FE]' // Violet
  },
  {
    title: '即梦AI视频',
    desc: '文本生成视频，静态图转视频，轻松制作创意短片。让静态的画面动起来，讲述更生动的故事。',
    image: '/plugin/即梦AI视频.png',
    gradient: 'from-[#DBEAFE] to-[#BFDBFE]' // Blue
  },
  {
    title: '大模型擂台',
    desc: '主流大模型能力评测与对比，助你选择最适合的模型。客观公正的评测数据，助您做出明智的技术选型。',
    image: '/plugin/大模型擂台.png',
    gradient: 'from-[#ECFCCB] to-[#D9F99D]' // Lime
  },
  {
    title: '小红书内容复刻',
    desc: '一键提取爆款笔记文案，智能仿写，快速产出高质量内容。轻松掌握流量密码，打造爆款账号。',
    image: '/plugin/小红书内容复刻.png',
    gradient: 'from-[#FFE4E6] to-[#FECDD3]' // Rose
  },
  {
    title: '模绘衣境',
    desc: 'AI服装设计与展示，虚拟试衣，缩短设计周期。无需制作样衣，即可预览穿着效果，降低设计成本。',
    image: '/plugin/模绘衣境.png',
    gradient: 'from-[#E0F2FE] to-[#BAE6FD]' // Sky Blue
  },
  {
    title: '热门视频混剪',
    desc: '智能抓取热门素材，自动混剪，快速生成短视频。紧跟热点趋势，轻松制作出爆款短视频。',
    image: '/plugin/热门视频混剪.png',
    gradient: 'from-[#F3E8FF] to-[#E9D5FF]' // Purple
  },
  {
    title: '爆款文章自动配图',
    desc: '根据文章内容自动匹配高质量图片，提升阅读体验。图文并茂，让您的文章更具吸引力。',
    image: '/plugin/爆款文章自动配图.png',
    gradient: 'from-[#FEF3C7] to-[#FDE68A]' // Amber
  }
]

const scrollContainer = ref<HTMLElement | null>(null)
const cardRefs = ref<HTMLElement[]>([])
let animationFrameId: number | null = null

// Drag functionality
const isDragging = ref(false)
const startX = ref(0)
const initialScrollLeft = ref(0)

const startDrag = (e: MouseEvent) => {
  isDragging.value = true
  if (scrollContainer.value) {
    startX.value = e.pageX - scrollContainer.value.offsetLeft
    initialScrollLeft.value = scrollContainer.value.scrollLeft
  }
}

const onDrag = (e: MouseEvent) => {
  if (!isDragging.value || !scrollContainer.value) return
  e.preventDefault()
  const x = e.pageX - scrollContainer.value.offsetLeft
  const walk = (x - startX.value) * 1.5 // Scroll-fast
  scrollContainer.value.scrollLeft = initialScrollLeft.value - walk
}

const stopDrag = () => {
  isDragging.value = false
}

const handleScroll = () => {
  if (animationFrameId) {
    cancelAnimationFrame(animationFrameId)
  }

  animationFrameId = requestAnimationFrame(() => {
    updateTransforms()
  })
}

const updateTransforms = () => {
  if (!scrollContainer.value) return

  const container = scrollContainer.value
  const viewportCenter = window.innerWidth / 2
  const containerRect = container.getBoundingClientRect()

  cardRefs.value.forEach((card) => {
    if (!card) return
    const rect = card.getBoundingClientRect()
    const cardCenter = rect.left + rect.width / 2

    // Calculate distance from center (normalized)
    // 1000px range for full rotation effect
    const range = 1000
    let dist = (cardCenter - viewportCenter) / range

    // Clamp distance
    if (dist < -1) dist = -1
    if (dist > 1) dist = 1

    // Easing for smoother curve
    const rotation = dist * 45 // Max 45 degrees rotation
    const translateZ = Math.abs(dist) * -200 // Push back up to 200px
    const scale = 1 - Math.abs(dist) * 0.1 // Scale down slightly at edges
    const opacity = 1 - Math.abs(dist) * 0.3 // Fade out slightly at edges

    card.style.transform = `perspective(1000px) rotateY(${rotation}deg) translateZ(${translateZ}px) scale(${scale})`
    card.style.opacity = `${opacity}`
  })
}

onMounted(() => {
  nextTick(() => {
    // Center the scroll initially
    if (scrollContainer.value) {
      const container = scrollContainer.value

      // Check if mobile (using simple width check)
      const isMobile = window.innerWidth < 640

      if (!isMobile) {
        const cardWidth = 360 + 32 // width + gap
        container.scrollLeft = (cardWidth * cards.length) / 2 - window.innerWidth / 2 + cardWidth / 2
      } else {
        // On mobile, maybe start at the beginning or slightly offset?
        // Let's just scroll to the second item to show there's more
        // container.scrollLeft = 0
      }

      updateTransforms()
    }

    window.addEventListener('resize', handleScroll)
  })
})

onUnmounted(() => {
  window.removeEventListener('resize', handleScroll)
  if (animationFrameId) {
    cancelAnimationFrame(animationFrameId)
  }
})
</script>

<style scoped>
.scrollbar-hide::-webkit-scrollbar {
    display: none;
}
.scrollbar-hide {
    -ms-overflow-style: none;
    scrollbar-width: none;
}
.perspective-container {
  perspective: 1000px;
  perspective-origin: center center;
}
.perspective-item {
  transform-style: preserve-3d;
  transition: transform 0.1s linear, opacity 0.1s linear; /* Short transition for smoothness during scroll */
}
</style>
