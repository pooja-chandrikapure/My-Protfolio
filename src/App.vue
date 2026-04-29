<script setup>

// import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <!-- <HelloWorld /> -->
   <router-view/>
</template>
<style scoped>
@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(24px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
