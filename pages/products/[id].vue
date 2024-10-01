<template>
  <div class="p-4">
    <h2 class="text-2xl font-bold mb-4">編輯產品</h2>
    <form @submit.prevent="saveProduct" class="max-w-md">
      <div class="mb-4">
        <label for="name" class="block mb-2">產品名稱</label>
        <input id="name" v-model="product.name" type="text" class="w-full p-2 border rounded" required>
      </div>
      <div class="mb-4">
        <label for="price" class="block mb-2">價格</label>
        <input id="price" v-model="product.price" type="number" step="0.01" class="w-full p-2 border rounded" required>
      </div>
      <div class="mb-4">
        <label for="stock" class="block mb-2">庫存</label>
        <input id="stock" v-model="product.stock" type="number" class="w-full p-2 border rounded" required>
      </div>
      <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">保存</button>
    </form>
  </div>
</template>

<script setup>
const route = useRoute();
const product = ref({
  id: route.params.id,
  name: '',
  price: 0,
  stock: 0,
});

// 模擬從 API 獲取產品數據
onMounted(() => {
  // 這裡應該是一個 API 調用
  product.value = {
    id: route.params.id,
    name: '產品 A',
    price: 99.99,
    stock: 100,
  };
});

const saveProduct = () => {
  // 這裡應該是一個 API 調用來保存產品
  console.log('保存產品:', product.value);
  // 保存成功後可以導航回產品列表頁面
  // navigateTo('/products');
};
</script>