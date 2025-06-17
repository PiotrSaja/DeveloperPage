<template>
  <div class="bg-slate-800 rounded-xl shadow-2xl overflow-hidden mb-12">

    <div class="terminal-header bg-slate-900 py-3 px-4 flex items-center justify-between">

      <div class="flex items-center space-x-3">
        <div class="flex space-x-1">
          <div class="w-3 h-3 rounded-full bg-red-500"></div>
          <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
          <div class="w-3 h-3 rounded-full bg-green-500"></div>
        </div>

        <div class="ml-4 text-slate-300 text-sm flex items-center gap-2">
          <i class="fas fa-file-code text-sky-400"></i>
          <span>DeveloperProfile.cs</span>
        </div>
      </div>

      <i class="fas fa-terminal text-slate-400 text-base"></i>
    </div>
    
    <div class="code-block bg-slate-900 p-6 min-h-[300px]">
      <pre class="font-['Fira_Code'] text-slate-200 text-sm md:text-base leading-relaxed whitespace-pre-wrap">
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
