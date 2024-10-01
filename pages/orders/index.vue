<template>
  <div class="p-4">
    <h2 class="text-2xl font-bold mb-4">訂單管理</h2>
    <table class="w-full bg-white shadow-md rounded">
      <thead>
        <tr class="bg-gray-200">
          <th class="p-2 text-left">訂單 ID</th>
          <th class="p-2 text-left">客戶</th>
          <th class="p-2 text-left">總金額</th>
          <th class="p-2 text-left">狀態</th>
          <th class="p-2 text-left">操作</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="order in orders" :key="order.id">
          <td class="p-2">{{ order.id }}</td>
          <td class="p-2">{{ order.customer }}</td>
          <td class="p-2">${{ order.total }}</td>
          <td class="p-2">{{ order.status }}</td>
          <td class="p-2">
            <button @click="viewOrderDetails(order.id)" class="text-blue-500 hover:underline">查看詳情</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const orders = ref([
  { id: 1, customer: '客戶 A', total: 299.97, status: '已付款' },
  { id: 2, customer: '客戶 B', total: 149.99, status: '處理中' },
  { id: 3, customer: '客戶 C', total: 399.98, status: '已發貨' },
]);

const viewOrderDetails = (orderId) => {
  // 這裡應該導航到訂單詳情頁面或打開一個模態框
  console.log('查看訂單詳情:', orderId);
};
</script>