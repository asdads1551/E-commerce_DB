<template>
  <aside class="bg-gray-100 w-64 min-h-screen p-4">
    <nav>
      <ul class="space-y-2">
        <li><NuxtLink to="/overview" class="block p-2 hover:bg-gray-200">總覽</NuxtLink></li>
        <li><NuxtLink to="/dashboard" class="block p-2 hover:bg-gray-200">儀表板</NuxtLink></li>
        <li><NuxtLink to="/products" class="block p-2 hover:bg-gray-200">產品管理</NuxtLink></li>
        <li><NuxtLink to="/orders" class="block p-2 hover:bg-gray-200">訂單管理</NuxtLink></li>
        <li><NuxtLink to="/customers" class="block p-2 hover:bg-gray-200">客戶管理</NuxtLink></li>
      </ul>
    </nav>
  </aside>
</template>