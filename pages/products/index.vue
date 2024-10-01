<template>
  <div class="p-4">
    <h2 class="text-2xl font-bold mb-4">產品管理</h2>
    <table class="w-full bg-white shadow-md rounded">
      <thead>
        <tr class="bg-gray-200">
          <th class="p-2 text-left">ID</th>
          <th class="p-2 text-left">名稱</th>
          <th class="p-2 text-left">價格</th>
          <th class="p-2 text-left">庫存</th>
          <th class="p-2 text-left">操作</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td class="p-2">{{ product.id }}</td>
          <td class="p-2">{{ product.name }}</td>
          <td class="p-2">${{ product.price }}</td>
          <td class="p-2">{{ product.stock }}</td>
          <td class="p-2">
            <NuxtLink :to="`/products/${product.id}`" class="text-blue-500 hover:underline">編輯</NuxtLink>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const products = ref([
  { id: 1, name: '產品 A', price: 99.99, stock: 100 },
  { id: 2, name: '產品 B', price: 149.99, stock: 50 },
  { id: 3, name: '產品 C', price: 199.99, stock: 75 },
]);
</script>