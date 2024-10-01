<template>
  <div class="p-4">
    <h2 class="text-2xl font-bold mb-4">庫存管理</h2>

    <!-- 庫存概覽 -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-8">
      <div v-for="stat in inventoryStats" :key="stat.label" class="bg-white p-4 rounded shadow">
        <h3 class="text-lg font-semibold text-gray-600">{{ stat.label }}</h3>
        <p class="text-2xl font-bold">{{ stat.value }}</p>
      </div>
    </div>

    <!-- 庫存列表 -->
    <div class="bg-white p-4 rounded shadow">
      <h3 class="text-xl font-bold mb-4">庫存列表</h3>
      <table class="w-full">
        <thead>
          <tr class="bg-gray-100">
            <th class="p-2 text-left">產品名稱</th>
            <th class="p-2 text-left">SKU</th>
            <th class="p-2 text-left">當前庫存</th>
            <th class="p-2 text-left">安全庫存</th>
            <th class="p-2 text-left">狀態</th>
            <th class="p-2 text-left">操作</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in inventoryItems" :key="item.id" class="border-b">
            <td class="p-2">{{ item.name }}</td>
            <td class="p-2">{{ item.sku }}</td>
            <td class="p-2">{{ item.currentStock }}</td>
            <td class="p-2">{{ item.safetyStock }}</td>
            <td class="p-2">
              <span :class="getStatusClass(item.status)">{{ item.status }}</span>
            </td>
            <td class="p-2">
              <button @click="updateStock(item.id)" class="text-blue-500 hover:underline">更新庫存</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
const inventoryStats = ref([
  { label: '總庫存產品', value: '1,234' },
  { label: '低庫存警告', value: '15' },
  { label: '缺貨產品', value: '3' },
]);

const inventoryItems = ref([
  { id: 1, name: '商品 A', sku: 'SKU001', currentStock: 100, safetyStock: 50, status: '正常' },
  { id: 2, name: '商品 B', sku: 'SKU002', currentStock: 30, safetyStock: 40, status: '低庫存' },
  { id: 3, name: '商品 C', sku: 'SKU003', currentStock: 0, safetyStock: 20, status: '缺貨' },
  { id: 4, name: '商品 D', sku: 'SKU004', currentStock: 200, safetyStock: 100, status: '正常' },
]);

const getStatusClass = (status) => {
  switch (status) {
    case '正常':
      return 'text-green-500';
    case '低庫存':
      return 'text-yellow-500';
    case '缺貨':
      return 'text-red-500';
    default:
      return '';
  }
};

const updateStock = (itemId) => {
  // 這裡應該打開一個模態框或導航到庫存更新頁面
  console.log('更新庫存:', itemId);
};
</script>