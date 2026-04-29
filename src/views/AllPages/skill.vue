<template>
  <section id="skills" class="ml-0 md:ml-[140px] px-6 md:px-12 py-16 bg-[#0a0a0a] text-white min-h-screen">

    <h2 class="text-2xl font-bold mb-8 underline decoration-[#800080] decoration-2 underline-offset-4">
      Skills
    </h2>

    <!-- Skill Category Cards -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 mb-10">

      <div v-for="category in skillCategories" :key="category.title"
        class="p-5 border border-white/10 bg-[#111] hover:border-[#800080] transition rounded hover:scale-[1.02] cursor-pointer">
        <h3 class="text-xs font-bold mb-3 bg-gradient-to-r from-[#eec5ee] to-[#800080] bg-clip-text text-transparent">
          {{ category.title }}
        </h3>
        <div class="flex flex-wrap gap-2">
          <span v-for="skill in category.skills" :key="skill"
            class="text-[10px] text-[#eec5ee] bg-[#800080]/10 border border-[#eec5ee]/20 rounded px-2 py-[3px] font-mono">
            {{ skill }}
          </span>
        </div>
      </div>

    </div>

    <!-- Skill Bars -->
    <div class="space-y-4 max-w-xl">
      <div v-for="item in skillBars" :key="item.name">
        <div class="flex justify-between text-xs text-gray-400 mb-1 font-mono">
          <span>{{ item.name }}</span>
          <span class="text-[#eec5ee]">{{ item.level }}%</span>
        </div>
        <div class="bg-white/5 rounded h-[5px]">
          <div class="h-[5px] rounded bg-gradient-to-r from-[#eec5ee] to-[#800080] transition-all duration-700"
            :style="{ width: item.level + '%' }">
          </div>
        </div>
      </div>
    </div>

  </section>
</template>

<script setup>
const skillCategories = [
  {
    title: 'Frontend',
    skills: ['Vue.js', 'JavaScript', 'HTML5', 'CSS3', 'Tailwind']
  },
  {
    title: 'Tools & Workflow',
    skills: ['Git', 'GitHub', 'VS Code', 'Figma', 'Postman']
  },
  {
    title: 'Concepts',
    skills: ['REST API', 'Responsive Design', 'Component Design', 'Performance']
  }
]

const skillBars = [
  { name: 'Vue.js', level: 90 },
  { name: 'JavaScript', level: 80 },
  { name: 'HTML & CSS', level: 95 },
  { name: 'Tailwind CSS', level: 85 }
]
</script>
