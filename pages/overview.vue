<template>
  <div class="p-4">
    <h2 class="text-2xl font-bold mb-4">總覽</h2>
    
    <!-- 快速統計 -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 mb-8">
      <div v-for="stat in quickStats" :key="stat.label" class="bg-white p-4 rounded shadow">
        <h3 class="text-lg font-semibold text-gray-600">{{ stat.label }}</h3>
        <p class="text-2xl font-bold">{{ stat.value }}</p>
      </div>
    </div>

    <!-- 主要功能區 -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mb-8">
      <NuxtLink v-for="feature in mainFeatures" :key="feature.title" :to="feature.link" class="bg-white p-6 rounded shadow hover:shadow-md transition-shadow">
        <h3 class="text-xl font-bold mb-2">{{ feature.title }}</h3>
        <p class="mb-4 text-gray-600">{{ feature.description }}</p>
        <span class="text-blue-500 hover:underline">進入 {{ feature.title }} &rarr;</span>
      </NuxtLink>
    </div>

    <!-- 最近活動 -->
    <div class="bg-white p-6 rounded shadow mb-8">
      <h3 class="text-xl font-bold mb-4">最近活動</h3>
      <ul class="space-y-2">
        <li v-for="activity in recentActivities" :key="activity.id" class="flex justify-between items-center border-b pb-2">
          <span>{{ activity.description }}</span>
          <span class="text-sm text-gray-500">{{ activity.time }}</span>
        </li>
      </ul>
    </div>

    <!-- 待辦事項 -->
    <div class="bg-white p-6 rounded shadow">
      <h3 class="text-xl font-bold mb-4">待辦事項</h3>
      <ul class="space-y-2">
        <li v-for="todo in todos" :key="todo.id" class="flex items-center">
          <input type="checkbox" :id="'todo-' + todo.id" v-model="todo.completed" class="mr-2">
          <label :for="'todo-' + todo.id" :class="{ 'line-through': todo.completed }">{{ todo.text }}</label>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
const quickStats = ref([
  { label: '今日銷售額', value: '$5,670' },
  { label: '本月訂單', value: '237' },
  { label: '新客戶', value: '18' },
  { label: '庫存警告', value: '3' },
]);

const mainFeatures = [
  { title: '儀表板', description: '查看關鍵業務指標和統計數據', link: '/dashboard' },
  { title: '產品管理', description: '管理產品目錄、價格和庫存', link: '/products' },
  { title: '訂單管理', description: '查看和處理客戶訂單', link: '/orders' },
  { title: '客戶管理', description: '管理客戶資料和訂單歷史', link: '/customers' },
  { title: '庫存管理', description: '跟踪和更新產品庫存', link: '/inventory' },
  { title: '報表分析', description: '生成銷售和業績報表', link: '/reports' },
];

const recentActivities = ref([
  { id: 1, description: '新訂單 #1234 已創建', time: '10 分鐘前' },
  { id: 2, description: '產品 "手機殼" 庫存不足', time: '1 小時前' },
  { id: 3, description: '客戶 John Doe 更新了個人資料', time: '2 小時前' },
  { id: 4, description: '完成了 5 筆訂單發貨', time: '昨天' },
]);

const todos = ref([
  { id: 1, text: '處理待發貨訂單', completed: false },
  { id: 2, text: '回覆客戶郵件', completed: true },
  { id: 3, text: '更新產品描述', completed: false },
  { id: 4, text: '審核新供應商申請', completed: false },
]);
</script>