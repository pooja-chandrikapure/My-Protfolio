<template>
  <section id="work" class="ml-0 md:ml-[140px] px-6 md:px-12 py-16 bg-[#0a0a0a] text-white min-h-screen">

    <h2 class="text-2xl font-bold mb-10 underline decoration-[#800080] decoration-2 underline-offset-4">
      Work Experience
    </h2>

    <!-- Timeline -->
    <div class="relative pl-6 border-l border-[#800080]/30">

      <div v-for="(job, index) in jobs" :key="index" class="relative mb-10">

        <!-- Dot -->
        <div class="absolute -left-[1.55rem] top-1 w-[10px] h-[10px] rounded-full bg-[#800080] ring-2 ring-[#800080] ring-offset-2 ring-offset-[#0a0a0a]"></div>

        <!-- Date -->
        <p class="text-[12px] text-white tracking-widest mb-1 font-mono uppercase font-bold">
          {{ job.date }}
        </p>

        <!-- Role -->
        <h3 class="text-sm font-bold text-white mb-[2px]">{{ job.role }}</h3>

        <!-- Company -->
        <p class="text-xs text-[#eec5ee] mb-3">{{ job.company }}</p>

        <!-- Description -->
        <p class="text-xs text-gray-400 leading-7 mb-3 font-mono">{{ job.description }}</p>

        <!-- Tags -->
        <div class="flex flex-wrap gap-2">
          <span v-for="tag in job.tags" :key="tag"
            class="text-[10px] text-[#eec5ee] bg-[#800080]/10 border border-[#eec5ee]/20 rounded px-2 py-[3px] font-mono">
            {{ tag }}
          </span>
        </div>
        <a v-if="job.link" :href="job.link" target="_blank"
            class="inline-flex items-center gap-1 mt-3 text-[10px] text-white border border-[#800080]/40 hover:border-[#800080] hover:bg-[#800080]/10 rounded px-3 py-1 transition font-mono">
            <span>View Project</span>
            <svg xmlns="http://www.w3.org/2000/svg" class="w-3 h-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M14 3h7m0 0v7m0-7L10 14M5 5H3a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-2" />
            </svg>
            </a>
            <a v-if="job.landing" :href="job.landing" target="_blank"
            class="inline-flex items-center gap-1 mt-3 text-[10px] text-white border border-[#800080]/40 hover:border-[#800080] hover:bg-[#800080]/10 rounded px-3 py-1 transition font-mono ml-2">
            <span>View Landing</span>
            <svg xmlns="http://www.w3.org/2000/svg" class="w-3 h-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M14 3h7m0 0v7m0-7L10 14M5 5H3a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-2" />
            </svg>
            </a>

      </div>
    </div>

  </section>
</template>

<script setup>
const jobs = [
  {
    date: 'Jan 2026 — Present',
    role: 'Frontend Developer Executive',
    company: 'Xtention Crew Technology',
    description: 'Built and maintained UI components for HRMS . Integrated REST APIs, handled state management, and improved performance across modules. Designed and developed responsive landing pages',
    tags: ['Vue.js', 'Tailwind', 'REST API', 'Git', 'Socket.io'],
    link: 'https://admin.qbitfinances.com/' ,
    landing: 'https://leads.verifiedpips.com/'
  },
  {
    date: 'Feb 2025 — July 2025',
    role: 'Frontend Developer Intern',
    company: 'Divyal Technologies Pvt. Ltd.',
    description: 'Developed the Parking Services Dashboard including modules for Event Management, Car Parking, Pricing, and Routes. Built responsive UI components, integrated REST APIs, and ensured smooth user experience across all modules.',
    tags: ['Vue.js','Tailwind CSS', 'JavaScript', 'TortoiseGit'],
    link:'https://staging-parking-services.tracsis.com/',
  }
]
</script>
