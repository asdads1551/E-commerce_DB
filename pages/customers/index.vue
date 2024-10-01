<template>
  <div class="p-4">
    <h2 class="text-2xl font-bold mb-4">客戶管理</h2>
    <table class="w-full bg-white shadow-md rounded">
      <thead>
        <tr class="bg-gray-200">
          <th class="p-2 text-left">ID</th>
          <th class="p-2 text-left">姓名</th>
          <th class="p-2 text-left">電子郵件</th>
          <th class="p-2 text-left">總訂單數</th>
          <th class="p-2 text-left">操作</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="customer in customers" :key="customer.id">
          <td class="p-2">{{ customer.id }}</td>
          <td class="p-2">{{ customer.name }}</td>
          <td class="p-2">{{ customer.email }}</td>
          <td class="p-2">{{ customer.totalOrders }}</td>
          <td class="p-2">
            <button @click="viewCustomerDetails(customer.id)" class="text-blue-500 hover:underline">查看詳情</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const customers = ref([
  { id: 1, name: '客戶 A', email: 'customerA@example.com', totalOrders: 5 },
  { id: 2, name: '客戶 B', email: 'customerB@example.com', totalOrders: 3 },
  { id: 3, name: '客戶 C', email: 'customerC@example.com', totalOrders: 7 },
]);

const viewCustomerDetails = (customerId) => {
  // 這裡應該導航到客戶詳情頁面或打開一個模態框
  console.log('查看客戶詳情:', customerId);
};
</script>