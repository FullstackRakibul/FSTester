<script setup lang="ts">
import {  ref } from 'vue';
const value2 = ref<string>('');

const handleChange = (value: string) => {
  console.log(`selected ${value}`);
};
const value = ref([]);
const options = [...Array(25)].map((_, i) => ({
  value: (i + 10).toString(36) + (i + 1),
}));


const columns = [
  {
    title: 'Item Name',
    dataIndex: 'name',
    width: '30%',
  },
  {
    title: 'Size',
    dataIndex: 'size',
    width: '15%',
  },
  {
    title: 'Detaisl',
    dataIndex: 'details',
    width: '40%',
  },
  {
    title: 'operation',
    dataIndex: 'operation',
  },
];

interface DataItem {
  key: string;
  name: string;
  size: number;
  details: string;
}
const data: DataItem[] = [];
for (let i = 0; i < 9; i++) {
  data.push({
    key: i.toString(),
    name: `Matt Fabric Type - ${i}`,
    size: 32,
    details: `matt no. ${i}`,
  });
}
const dataSource = ref(data);
const wrapperCol = { span: 14 };
const labelCol = { style: { width: '150px' } };
</script>

<template>
  <a-row gutter="16">
    <!-- Responsive Columns -->
    <a-col
      :xs="{ span: 24 }"
      :sm="{ span: 24 }"
      :md="{ span: 12 }"
      :lg="{ span: 6 }"
    >
      <a-card title="Start An Fabric Inspection" class="w-full">
        <div>
          <a-form
            :label-col="labelCol"
            :wrapper-col="wrapperCol"
            layout="horizontal"
            class="gap-12 space-y-4"
          >
            <a-select
              v-model:value="value"
              mode="tags"
              class="w-full"
              placeholder="Tags Mode"
              :options="options"
              @change="handleChange"
            />
            <a-textarea
              v-model:value="value2"
              placeholder="Autosize height with minimum and maximum number of lines"
              :auto-size="{ minRows: 2, maxRows: 5 }"
            />
          </a-form>
        </div>
      </a-card>
    </a-col>

    <a-col
      :xs="{ span: 24 }"
      :sm="{ span: 24 }"
      :md="{ span: 12 }"
      :lg="{ span: 18 }"
    >
      <a-card title="End-to-End Fabric Quality Inspection" class="w-full">
           <a-table :pagination="false" :columns="columns" :data-source="dataSource" bordered>
            
           </a-table> 
      </a-card>
    </a-col>
  </a-row>
</template>

<style scoped>
/* Add any additional custom styles here */
</style>
