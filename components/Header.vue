<template>
  <header class="bg-gray-800 text-white p-4">
    <nav class="container mx-auto flex justify-between items-center">
      <h1 class="text-xl font-bold">電商後台管理系統</h1>
      <ul class="flex space-x-4">
        <li><NuxtLink to="/overview">總覽</NuxtLink></li>
        <li><NuxtLink to="/dashboard">儀表板</NuxtLink></li>
        <li><NuxtLink to="/products">產品管理</NuxtLink></li>
        <li><NuxtLink to="/orders">訂單管理</NuxtLink></li>
        <li><NuxtLink to="/customers">客戶管理</NuxtLink></li>
      </ul>
    </nav>
  </header>
</template>