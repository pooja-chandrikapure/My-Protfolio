<template>
  <section id="contact" class="ml-0 md:ml-[140px] px-6 md:px-12 py-16 bg-[#0a0a0a] text-white min-h-screen">

    <h2 class="text-2xl font-bold mb-2 underline decoration-[#800080] decoration-2 underline-offset-4">
      Contact
    </h2>
    <p class="text-xs text-gray-400 font-mono mb-10">Feel free to reach out — I'd love to connect!</p>

    <div class="grid md:grid-cols-2 gap-10">

      <!-- Left: Contact Info -->
      <div class="space-y-5">

        <div v-for="item in contactInfo" :key="item.label"
          class="flex items-center gap-4 p-4 border border-white/10 bg-[#111] rounded hover:border-[#800080] transition cursor-pointer">
          <div class="w-8 h-8 rounded-full bg-[#800080]/15 border border-[#800080]/30 flex items-center justify-center flex-shrink-0">
            <span class="text-[#eec5ee] text-sm">{{ item.icon }}</span>
          </div>
          <div>
            <p class="text-[10px] text-[#800080] font-mono uppercase tracking-widest mb-[2px]">{{ item.label }}</p>
            <a v-if="item.href" :href="item.href" target="_blank"
              class="text-xs text-gray-300 hover:text-[#eec5ee] transition font-mono">
              {{ item.value }}
            </a>
            <p v-else class="text-xs text-gray-300 font-mono">{{ item.value }}</p>
          </div>
        </div>

        <!-- Social Links -->
        <div class="flex gap-3 mt-2">
          <a v-for="social in socials" :key="social.label" :href="social.href" target="_blank"
            class="flex items-center gap-2 text-[10px] text-[#eec5ee] bg-[#800080]/10 border border-[#eec5ee]/20 hover:border-[#800080] hover:bg-[#800080]/20 rounded px-3 py-2 transition font-mono">
            {{ social.label }} ↗
        </a>
        </div>

      </div>

      <!-- Right: Contact Form -->
      <div class="p-6 border border-white/10 bg-[#111] rounded hover:border-[#800080]/50 transition">

        <form @submit.prevent="handleSubmit" class="space-y-4">

          <div>
            <label class="block text-[10px] text-[#800080] font-mono uppercase tracking-widest mb-1">Name</label>
            <input v-model="form.name" type="text" placeholder="Your name"
              class="w-full bg-[#0a0a0a] border border-white/10 rounded px-3 py-2 text-xs text-gray-300 font-mono placeholder-gray-600 focus:outline-none focus:border-[#800080] transition" />
          </div>

          <div>
            <label class="block text-[10px] text-[#800080] font-mono uppercase tracking-widest mb-1">Email</label>
            <input v-model="form.email" type="email" placeholder="your@email.com"
              class="w-full bg-[#0a0a0a] border border-white/10 rounded px-3 py-2 text-xs text-gray-300 font-mono placeholder-gray-600 focus:outline-none focus:border-[#800080] transition" />
          </div>

          <div>
            <label class="block text-[10px] text-[#800080] font-mono uppercase tracking-widest mb-1">Message</label>
            <textarea v-model="form.message" rows="5" placeholder="Write your message..."
              class="w-full bg-[#0a0a0a] border border-white/10 rounded px-3 py-2 text-xs text-gray-300 font-mono placeholder-gray-600 focus:outline-none focus:border-[#800080] transition resize-none"></textarea>
          </div>

          <button type="submit"
            class="w-full py-2 text-xs font-mono font-bold text-[#eec5ee] border border-[#800080]/50 hover:bg-[#800080]/20 hover:border-[#800080] rounded transition">
            Send Message ↗
          </button>

          <!-- Success Message -->
          <p v-if="submitted" class="text-[10px] text-[#eec5ee] font-mono text-center mt-2">
            ✓ Message sent! I'll get back to you soon.
          </p>

        </form>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const form = ref({ name: '', email: '', message: '' })
const submitted = ref(false)

const contactInfo = [
  {
    label: 'Email',
    value: 'poojachandrikapure3011@email.com',
    href: 'mailto:poojachandrikapure3011@email.com',
    icon: '✉'
  },
  {
    label: 'Phone',
    value: '+91 9131685953',
    href: null,
    icon: '📞'
  },
  {
    label: 'Location',
    value: 'India',
    href: null,
    icon: '📍'
  }
]

const socials = [
  {
    label: 'GitHub',
    href: 'https://github.com/pooja-chandrikapure',
  },
  {
    label: 'LinkedIn',
    href: 'https://www.linkedin.com/in/pooja-chandrikapure-98b117220',
  }
]

const handleSubmit = async () => {
  if (!form.value.name || !form.value.email || !form.value.message) return
  await fetch('https://formspree.io/f/xojydvka', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(form.value)
  })
  submitted.value = true
  form.value = { name: '', email: '', message: '' }
  setTimeout(() => submitted.value = false, 4000)
}
// const handleSubmit = () => {
//   if (!form.value.name || !form.value.email || !form.value.message) return
//   const subject = encodeURIComponent(`Portfolio message from ${form.value.name}`)
//   const body = encodeURIComponent(form.value.message)
//   window.location.href = `mailto:pooja@email.com?subject=${subject}&body=${body}`
// }
</script>
