<template>
  <div class="bg-slate-850 rounded-xl shadow-xl overflow-hidden mb-12 border border-slate-700">

    <!-- Terminal Header -->
    <div class="bg-slate-900 px-4 py-3 flex items-center justify-between border-b border-slate-700">

      <!-- Window Controls + Filename -->
      <div class="flex items-center gap-4">
        <!-- Mac-style buttons -->
        <div class="flex gap-1">
          <div class="w-3 h-3 rounded-full bg-red-500"></div>
          <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
          <div class="w-3 h-3 rounded-full bg-green-500"></div>
        </div>

        <!-- File Label -->
        <div class="flex items-center gap-2 text-slate-300 text-sm font-mono">
          <i class="fas fa-file-code text-sky-400"></i>
          <span class="tracking-tight">DeveloperProfile.cs</span>
        </div>
      </div>

      <!-- Terminal Icon -->
      <i class="fas fa-terminal text-slate-500 text-sm"></i>
    </div>

    <!-- Code Area -->
    <div class="bg-slate-900 p-5 min-h-[280px] font-mono text-slate-200 text-sm leading-relaxed whitespace-pre-wrap">
      <pre class="whitespace-pre-wrap break-words">
<code>{{ typedCode }}<span v-if="isTyping" class="typewriter-cursor"></span></code>
      </pre>
    </div>
    
  </div>
</template>

<script setup>
defineProps({
  typedCode: String,
  isTyping: Boolean
})
</script>

<style scoped>
.typewriter-cursor {
  display: inline-block;
  width: 3px;
  background-color: #93c5fd;
  margin-left: 4px;
  height: 1.2em;
  animation: blink 1s infinite;
}

@keyframes blink {
  0% { opacity: 1; }
  50% { opacity: 0; }
  100% { opacity: 1; }
}
</style>
