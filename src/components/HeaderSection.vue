<template>
  <header class="text-center mb-12">
  <div class="flex justify-center mb-4">
    <img
      src="/profile.jpg"
      alt="Profile picture"
      class="w-24 h-24 md:w-36 md:h-36 rounded-full border-4 border-indigo-500 shadow-lg"
    />
  </div>

  <h1 class="text-4xl md:text-5xl font-bold text-white mb-3">{{ props.name }}</h1>
  <p class="text-xl text-slate-300">{{ props.role }}</p>

  <div class="mt-6 flex justify-center">
    <div class="w-24 h-1 bg-indigo-500 rounded-full"></div>
  </div>
</header>

</template>

<script setup>
const props = defineProps({
  name: String,
  role: String,
})
</script>
