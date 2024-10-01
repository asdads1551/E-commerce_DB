<template>
  <div class="p-4">
    <h2 class="text-2xl font-bold mb-4">報表分析</h2>

    <!-- 報表選擇器 -->
    <div class="mb-8">
      <label for="report-type" class="block mb-2">選擇報表類型：</label>
      <select id="report-type" v-model="selectedReport" class="w-full md:w-1/3 p-2 border rounded">
        <option v-for="report in reportTypes" :key="report.value" :value="report.value">
          {{ report.label }}
        </option>
      </select>
    </div>

    <!-- 報表內容 -->
    <div class="bg-white p-4 rounded shadow">
      <h3 class="text-xl font-bold mb-4">{{ getReportTitle() }}</h3>
      
      <!-- 銷售報表 -->
      <table v-if="selectedReport === 'sales'" class="w-full">
        <thead>
          <tr class="bg-gray-100">
            <th class="p-2 text-left">日期</th>
            <th class="p-2 text-left">訂單數</th>
            <th class="p-2 text-left">銷售額</th>
            <th class="p-2 text-left">平均訂單金額</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in salesData" :key="item.date" class="border-b">
            <td class="p-2">{{ item.date }}</td>
            <td class="p-2">{{ item.orders }}</td>
            <td class="p-2">${{ item.revenue.toFixed(2) }}</td>
            <td class="p-2">${{ (item.revenue / item.orders).toFixed(2) }}</td>
          </tr>
        </tbody>
      </table>

      <!-- 產品表現報表 -->
      <table v-if="selectedReport === 'products'" class="w-full">
        <thead>
          <tr class="bg-gray-100">
            <th class="p-2 text-left">產品名稱</th>
            <th class="p-2 text-left">銷售數量</th>
            <th class="p-2 text-left">銷售額</th>
            <th class="p-2 text-left">利潤</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in productData" :key="item.name" class="border-b">
            <td class="p-2">{{ item.name }}</td>
            <td class="p-2">{{ item.quantity }}</td>
            <td class="p-2">${{ item.revenue.toFixed(2) }}</td>
            <td class="p-2">${{ item.profit.toFixed(2) }}</td>
          </tr>
        </tbody>
      </table>

      <!-- 客戶分析報表 -->
      <table v-if="selectedReport === 'customers'" class="w-full">
        <thead>
          <tr class="bg-gray-100">
            <th class="p-2 text-left">客戶名稱</th>
            <th class="p-2 text-left">訂單數</th>
            <th class="p-2 text-left">總消費額</th>
            <th class="p-2 text-left">平均訂單金額</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in customerData" :key="item.name" class="border-b">
            <td class="p-2">{{ item.name }}</td>
            <td class="p-2">{{ item.orders }}</td>
            <td class="p-2">${{ item.totalSpent.toFixed(2) }}</td>
            <td class="p-2">${{ (item.totalSpent / item.orders).toFixed(2) }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
const reportTypes = [
  { label: '銷售報表', value: 'sales' },
  { label: '產品表現報表', value: 'products' },
  { label: '客戶分析報表', value: 'customers' },
];

const selectedReport = ref('sales');

const salesData = ref([
  { date: '2023-04-01', orders: 45, revenue: 5670.50 },
  { date: '2023-04-02', orders: 52, revenue: 6234.75 },
  { date: '2023-04-03', orders: 38, revenue: 4890.25 },
  { date: '2023-04-04', orders: 60, revenue: 7560.00 },
]);

const productData = ref([
  { name: '商品 A', quantity: 150, revenue: 14925.00, profit: 4477.50 },
  { name: '商品 B', quantity: 80, revenue: 11960.00, profit: 3588.00 },
  { name: '商品 C', quantity: 120, revenue: 23880.00, profit: 7164.00 },
  { name: '商品 D', quantity: 200, revenue: 19900.00, profit: 5970.00 },
]);

const customerData = ref([
  { name: '客戶 A', orders: 5, totalSpent: 2500.00 },
  { name: '客戶 B', orders: 3, totalSpent: 1800.00 },
  { name: '客戶 C', orders: 8, totalSpent: 4000.00 },
  { name: '客戶 D', orders: 2, totalSpent: 1000.00 },
]);

const getReportTitle = () => {
  const report = reportTypes.find(r => r.value === selectedReport.value);
  return report ? report.label : '';
};
</script>