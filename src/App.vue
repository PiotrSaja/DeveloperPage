<template>
  <main>
    <div class="min-h-screen min-w-screen bg-gradient-to-br from-slate-900 to-slate-800 flex items-center justify-center p-4">
      <div class="w-full max-w-4xl">
        <HeaderSection :name="name" :role="role"/>
        <Terminal :typedCode="typedCode" :isTyping="isTyping" />
        <SocialLinks :links="visibleLinks" />
        <footer class="mt-12 text-center text-slate-400">
          <p>Designed by {{ designedBy }} - {{ new Date().getFullYear() }}</p>
        </footer>
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import autoAnimate from '@formkit/auto-animate'

import HeaderSection from './components/HeaderSection.vue'
import Terminal from './components/Terminal.vue'
import SocialLinks from './components/SocialLinks.vue'

const name = 'Piotr Saja'
const role = '.NET Fullstack Developer'
const designedBy = 'saja.dev'

const socialLinks = [
  {
    name: 'GitHub',
    username: '@PiotrSaja',
    url: 'https://github.com/PiotrSaja',
    icon: 'fab fa-github',
    iconColor: 'text-slate-300'
  },
  {
    name: 'LinkedIn',
    username: '@piotr-saja',
    url: 'https://www.linkedin.com/in/piotr-saja',
    icon: 'fab fa-linkedin',
    iconColor: 'text-blue-400'
  },
]

const code = `public class DeveloperProfile
{
    public static void Main()
    {
        // General Information
        string location = "Rzeszów, Poland";
        string[] skills = { "C#", "Vue", ".NET", "Azure", 'K8S' };
        string currentRole = "Fullstack Developer at EnterAir S.A.";
        
        Console.WriteLine($"Based in {location}");
        Console.WriteLine($"Current Role: {currentRole}");
        Console.WriteLine("Skills: " + string.Join(", ", skills));

        // Social Media
        Dictionary<string, string> socialLinks = new Dictionary<string, string>()
        {
            ${socialLinks.map(link => `{ "${link.name}", "${link.url}" }`).join(',\n            ')}
        };

        Console.WriteLine("Connect with me:");
        foreach (var link in socialLinks)
        {
            Console.WriteLine($"{link.Key}: {link.Value}");
        }
    }
}`

const typedCode = ref('')
const isTyping = ref(true)
const visibleLinks = ref([])

const typeCodeAnimation = () => {
  const typingSpeed = 15
  let i = 0

  const type = () => {
    if (i < code.length) {
      typedCode.value += code[i++]
      setTimeout(type, typingSpeed)
    } else {
      isTyping.value = false
      showSocialLinks()
    }
  }

  setTimeout(type, 500)
}

const showSocialLinks = () => {
  socialLinks.forEach((link, idx) => {
    setTimeout(() => visibleLinks.value.push(link), idx * 300)
  })
}

onMounted(() => {
  typeCodeAnimation()
})
</script>
