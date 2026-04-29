<template>
  <div class="flex min-h-screen bg-[#0a0a0a] text-white">
    <sideNavbar />

    <main
      class="ml-[140px] flex-1 min-h-screen relative flex flex-col justify-center px-[5vw] overflow-hidden max-[768px]:ml-0 max-[768px]:px-6 max-[768px]:pt-24 max-[768px]:pb-8"
    >
      <!-- Code tags -->
      <span class="code-tag absolute top-[7%] left-[5%] font-mono text-[0.8rem] text-white/[0.18] pointer-events-none select-none max-[768px]:hidden">&lt;/html&gt;</span>
      <span class="code-tag absolute top-[15%] left-[5%] font-mono text-[0.8rem] text-white/[0.18] pointer-events-none select-none max-[768px]:hidden">&lt;body&gt;</span>
      <span class="code-tag absolute top-[28%] left-[5%] font-mono text-[0.8rem] text-white/[0.18] pointer-events-none select-none max-[768px]:hidden">&lt;h1&gt;</span>
      <span class="code-tag absolute top-[72%] left-[5%] font-mono text-[0.8rem] text-white/[0.18] pointer-events-none select-none max-[768px]:hidden">&lt;/h1&gt;</span>
      <span class="code-tag absolute top-[75%] left-[5%] font-mono text-[0.8rem] text-white/[0.18] pointer-events-none select-none max-[768px]:hidden">&lt;p&gt;</span>
      <span class="code-tag absolute top-[83%] left-[5%] font-mono text-[0.8rem] text-white/[0.18] pointer-events-none select-none max-[768px]:hidden">&lt;/p&gt;</span>

      <!-- Headline -->
      <div class="flex flex-col gap-0 z-[2] fade-up">
        <h1 class="font-['Sora'] font-extrabold text-white m-0 leading-[1.1] text-[clamp(2.5rem,6vw,5rem)]">Hi,</h1>
        <h1 class="font-['Sora'] font-extrabold text-white m-0 leading-[1.1] text-[clamp(2.5rem,6vw,5rem)]">
          I'm <span class="text-[#eec5ee]">P</span>ooja
        </h1>
        <h1 class="font-['Sora'] font-extrabold text-white m-0 leading-[1.1] text-[clamp(2.5rem,6vw,5rem)]">
          Frontend de<span class="text-[#800080]">v</span>eloper
        </h1>
      </div>

      <!-- Subline -->
      <div class="flex flex-col mt-5 z-[2] fade-up [animation-delay:0.2s]">
        <span class="font-mono text-[0.8rem] text-white/[0.18] pointer-events-none select-none max-[768px]:hidden">&lt;p&gt;</span>
        <p class="font-mono text-[0.85rem] text-[#888] my-[0.15rem] tracking-[0.04em]">
          Front End Developer / Vue.js Expert
        </p>
        <span class="font-mono text-[0.8rem] text-white/[0.18] pointer-events-none select-none max-[768px]:hidden">&lt;/p&gt;</span>
      </div>

      <!-- CTA Button -->
      <a
        href="#contact"
        class="inline-block mt-9 px-8 py-3 border border-[#800080] text-[#ffd7ff] bg-gradient-to-br from-[#800080] to-[#ebaeeb] font-mono text-[0.85rem] tracking-[0.08em] no-underline transition-[background,color] duration-[250ms] ease-[ease] w-fit z-[2] hover:bg-[#800080] hover:text-white fade-up [animation-delay:0.4s]"
      >
        Contact me!
      </a>

      <!-- Swirl canvas -->
      <div
        class="absolute right-[-80px] top-1/2 -translate-y-1/2 w-[680px] h-[680px] pointer-events-none opacity-100 max-[768px]:w-[340px] max-[768px]:h-[340px] max-[768px]:right-[-60px] max-[768px]:opacity-50"
        aria-hidden="true"
      >
        <canvas ref="swirlCanvas" class="w-full h-full"></canvas>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import sideNavbar from '../../components/sideNavbar.vue'

const swirlCanvas = ref(null)

onMounted(() => {
  const canvas = swirlCanvas.value
  if (!canvas) return
  const ctx = canvas.getContext('2d')

  canvas.width = 700
  canvas.height = 700

  let t = 0
  const totalLines = 200
  const lines = Array.from({ length: totalLines }, (_, i) => ({
    offset: (i / totalLines) * Math.PI * 2
  }))

  function draw() {
    ctx.fillStyle = 'rgba(10, 10, 10, 0.18)'
    ctx.fillRect(0, 0, canvas.width, canvas.height)

    const cx = canvas.width / 2
    const cy = canvas.height / 2

    lines.forEach((line, i) => {
      const phase = line.offset + t * 0.5
      const wave = Math.sin(t * 0.4 + i * 0.03)

      const r1 = 90 + Math.sin(phase * 1.2 + t * 0.2) * 170
      const r2 = 110 + Math.cos(phase * 0.85 + 1.2) * 180
      const a1 = phase
      const a2 = phase + 0.75 + wave * 0.35

      const x1 = cx + Math.cos(a1) * r1
      const y1 = cy + Math.sin(a1) * r1 * 0.52
      const x2 = cx + Math.cos(a2) * r2
      const y2 = cy + Math.sin(a2) * r2 * 0.52

      const alpha1 = 0.18 + Math.sin(phase + i * 0.5) * 0.12
      ctx.beginPath()
      ctx.moveTo(x1, y1)
      ctx.lineTo(x2, y2)
      ctx.strokeStyle = `rgba(128, 0, 128, ${Math.max(0.06, alpha1)})`
      ctx.lineWidth = 0.9
      ctx.stroke()

      if (i % 2 === 0) {
        const r3 = 30 + Math.sin(phase * 2 + t * 0.3) * 80
        const r4 = 50 + Math.cos(phase * 1.5 + 0.8) * 90
        const a3 = phase * 1.1 + t * 0.15
        const a4 = a3 + 0.5 + wave * 0.2

        const x3 = cx + Math.cos(a3) * r3
        const y3 = cy + Math.sin(a3) * r3 * 0.5
        const x4 = cx + Math.cos(a4) * r4
        const y4 = cy + Math.sin(a4) * r4 * 0.5

        const alpha2 = 0.22 + Math.sin(phase * 1.5 + i) * 0.1
        ctx.beginPath()
        ctx.moveTo(x3, y3)
        ctx.lineTo(x4, y4)
        ctx.strokeStyle = `rgba(128, 0, 128, ${Math.max(0.08, alpha2)})`
        ctx.lineWidth = 0.6
        ctx.stroke()
      }
    })

    t += 0.01
    requestAnimationFrame(draw)
  }

  draw()
})
</script>

<style>
/* Google Fonts import */
@import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Sora:wght@400;700;800&display=swap');

/* fadeUp animation only — everything else is Tailwind */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}

.fade-up {
  animation: fadeUp 0.9s ease both;
}
</style>
