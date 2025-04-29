<template>
  <header>
    <MenuNav />
    <div class="container">
      <div></div>
    </div>
  </header>
  <section>
    <router-view />
  </section>
  <footer>
    <div>2025.04.22 소영재의 프로젝트</div>
  </footer>
</template>
<script setup>
import MenuNav from "@/components/MenuNav.vue";
</script>
