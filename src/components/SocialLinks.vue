<template>
  <div class="grid grid-cols-2 gap-4" ref="container">
    <a
      v-for="(link, index) in links"
      :key="index"
      :href="link.url"
      target="_blank"
      class="social-link bg-slate-800 rounded-xl p-6 flex flex-col items-center justify-center text-center hover:bg-slate-700 transition-colors duration-300"
    >
      <div class="text-3xl mb-3" :class="link.iconColor">
        <i :class="link.icon"></i>
      </div>
      <h3 class="text-xl font-semibold text-white mb-1">{{ link.name }}</h3>
      <p class="text-slate-400 text-sm">{{ link.username }}</p>
    </a>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import autoAnimate from '@formkit/auto-animate'

const props = defineProps({
  links: Array
})

const container = ref(null)

onMounted(() => {
  if (container.value) autoAnimate(container.value)
})
</script>

<style scoped>
.social-link {
  transition: all 0.3s ease;
  transform-origin: center;
}
.social-link:hover {
  transform: translateY(-5px) scale(1.05);
  box-shadow: 0 10px 25px -5px rgba(59, 130, 246, 0.4);
}
</style>
