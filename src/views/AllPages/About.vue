<template>
  <section id="about" class="ml-0 md:ml-[140px] px-6 md:px-12 py-16 bg-[#0a0a0a] text-white min-h-screen">

    <!-- Title -->
    <h2 class="text-2xl font-bold mb-8 underline decoration-[#800080] decoration-2 underline-offset-4">
      About Me
    </h2>

    <!-- Content -->
    <div class="grid md:grid-cols-2 gap-10">

      <!-- Left Side -->
      <div class="space-y-4 text-sm leading-7 text-gray-400 font-mono">
        <p>
          Hi, I’m <span class="text-[#eec5ee] font-semibold">Pooja</span>, a passionate 
          <strong class="text-white">Frontend Developer</strong> who enjoys building clean,
          responsive, and user-friendly web applications.
        </p>

        <p>
          I specialize in <strong class="text-white">Vue.js</strong> and modern frontend
          technologies. I love transforming complex ideas into simple,
          intuitive interfaces.
        </p>

        <p>
          I’ve worked on real-world projects like HRMS systems and Parking Services Dashboards,
          where I handled UI development, API integration, and performance optimization.
        </p>

        <p>
          Currently, I’m looking for opportunities where I can grow,
          contribute, and build impactful digital experiences.
        </p>
      </div>

      <!-- Right Side Cards -->
      <div class="flex flex-col gap-4">

        <!-- Skills -->
       <div class="p-5 border border-white/10 bg-[#111] hover:border-[#800080] transition rounded shadow hover:shadow-lg hover:scale-[1.02] cursor-pointer">
        <h3 class="text-sm font-bold mb-3 bg-gradient-to-r from-[#eec5ee] to-[#800080] bg-clip-text text-transparent">
            Skills
        </h3>
        <div class="flex flex-wrap gap-2">
            <span v-for="skill in ['Vue.js', 'JavaScript', 'HTML', 'CSS', 'Tailwind','Socket.io', 'GitHub','Vuetify']" :key="skill"
            class="text-[10px] text-[#eec5ee] bg-[#800080]/10 border border-[#eec5ee]/20 rounded px-2 py-[3px]">
            {{ skill }}
            </span>
        </div>
        </div>

        <!-- Experience -->
        <div class="p-5 border border-white/10 bg-[#111] hover:border-[#800080] transition rounded shadow hover:shadow-lg hover:scale-[1.02] transition cursor-pointer">
          <h3 class="text-sm font-bold mb-1 bg-gradient-to-r from-[#eec5ee] to-[#800080] bg-clip-text text-transparent">
            Experience
          </h3>
          <p class="text-xs text-gray-400">
            Internship + Real-world project development
          </p>
        </div>

        <!-- Projects -->
        <div class="p-5 border border-white/10 bg-[#111] hover:border-[#800080] transition rounded shadow hover:shadow-lg hover:scale-[1.02] transition cursor-pointer">
          <h3 class="text-sm font-bold mb-2 bg-gradient-to-r from-[#eec5ee] to-[#800080] bg-clip-text text-transparent">
            Projects
          </h3>

          <ul class="text-xs text-gray-400 space-y-1">
            <li>• HRMS Dashboard (Employee Attendance + Project Management System  + Payroll System + Ticket System )</li>
            <li>• Parking Service Dashboard (Event Management + Payment System + Car Parking + Routes + Allocation)</li>
            <li>• Responsive Landing Pages</li>
          </ul>
        </div>

        <!-- Focus -->
        <div class="p-5 border border-white/10 bg-[#111] hover:border-[#800080] transition rounded shadow hover:shadow-lg hover:scale-[1.02] transition cursor-pointer"">
          <h3 class="text-sm font-bold mb-1 bg-gradient-to-r from-[#eec5ee] to-[#800080] bg-clip-text text-transparent">
            Focus
          </h3>
          <p class="text-xs text-gray-400">
            Building scalable UI & improving user experience
          </p>
        </div>

      </div>
    </div>

  </section>
</template>

<script setup>
// no logic needed
</script>
