<template>
  <div class="min-h-screen flex flex-col">
    <Header />
    
    <div class="flex flex-1">
      <Sidebar />
      
      <main class="flex-1 bg-gray-50">
        <NuxtPage />
      </main>
    </div>
    
    <footer class="bg-gray-800 text-white p-4 text-center">
      <p>&copy; 2023 電商後台管理系統. 版權所有.</p>
    </footer>
    
    <NuxtRouteAnnouncer />
  </div>
</template>

<script setup>
import Header from '~/components/Header.vue';
import Sidebar from '~/components/Sidebar.vue';
import { useRouter } from 'vue-router';

const router = useRouter();

// 如果是根路徑，重定向到總覽頁面
if (process.client) {
  router.beforeEach((to, from, next) => {
    if (to.path === '/') {
      next('/overview');
    } else {
      next();
    }
  });
}
</script>
