<script setup lang="ts">
import {  ref } from 'vue';
const value2 = ref<string>('');

const handleChange = (value: string) => {
  console.log(`selected ${value}`);
};
const value = ref([]);
const options = [...Array(25)].map((_, i) => ({
  value: `কাপড় টাইপ -`+(i + 10).toString() + (i + 1),
}));


const columns = [
  {
    title: 'ধরনের নাম',
    dataIndex: 'name',
    width: '30%',
  },
  {
    title: 'মাপ',
    dataIndex: 'size',
    width: '15%',
  },
  {
    title: 'মন্তব্য ও বর্ণনা',
    dataIndex: 'details',
    width: '40%', 
  },
  {
    title: 'অপারেশন',
    dataIndex: 'operation',
    render:[

    ]
  },
];

const value12 = ref<string>('');
const value13 = ref<string>('');
const value14 = ref<string>('');
const value7 = ref<string>('input content');
const value8 = ref<string | null>(null)

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
    name: ` ম্যাট এর ফেব্রেকিল এর ধরম নাম্বার - ${i}`,
    size: 32,
    details: ` ম্যাট নাম্বার . ${i}`,
  });
}
const dataSource = ref(data);
const wrapperCol = { span: 24 };
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
  <a-card
    title="ফ্যাব্রিক পরিদর্শন শুরু করুন"
    class="w-full text-6xl"
    style="font-family: 'Hind Siliguri', sans-serif; line-height: 1.5; font-weight: 350;"
    :headStyle="{ backgroundColor: '#0D7C66', color: 'white' }"
  >
    <div>
      <a-form
        :label-col="labelCol"
        :wrapper-col="wrapperCol"
        layout="horizontal"
        class="gap-12 space-y-4"
        style="font-family: 'Hind Siliguri', sans-serif;"
      >
        <!-- Form Items -->
        <a-form-item class="w-full">
          <a-select
            v-model:value="value"
            mode="tags"
            class="w-full"
            placeholder="ট্যাগ মোড"
            :options="options"
            @change="handleChange"
            style="font-family: 'Hind Siliguri', sans-serif;"
          />
        </a-form-item>
        
        <a-form-item class="w-full">
          <a-input-group compact class="w-full">
            <a-textarea
              v-model:value="value2"
              placeholder="সংক্ষিপ্ত বিবরণী লিখুন ..."
              :auto-size="{ minRows: 2, maxRows: 5 }"
              class="w-full"
            />
          </a-input-group>
        </a-form-item>
        
        <a-form-item class="w-full">
          <a-input-group compact class="w-full">
            <a-input
              v-model:value="value12"
              style="width: 40%; text-align: center; font-family: 'Hind Siliguri', sans-serif;"
              placeholder="দৈর্ঘ্য"
            />
            <a-input
              v-model:value="value13"
              class="site-input-split"
              style="width: 20%; border-left: 0; pointer-events: none; font-family: 'Hind Siliguri', sans-serif;"
              placeholder="~"
              disabled
            />
            <a-input
              v-model:value="value14"
              class="site-input-right"
              style="width: 40%; text-align: center; font-family: 'Hind Siliguri', sans-serif;"
              placeholder="প্রস্থ"
            />
          </a-input-group>
        </a-form-item>
        
        <a-form-item class="w-full">
          <a-input-group compact class="w-full">
            <a-date-picker v-model:value="value8" style="width: 100%; font-family: 'Hind Siliguri', sans-serif;" />
          </a-input-group>
        </a-form-item>
        
        <a-form-item class="w-full">
          <a-button type="primary" html-type="submit" class="w-full 
          login-form-button"
           style="font-family: 'Hind Siliguri', sans-serif;background-color: #0D7C66;"
          >
            প্রক্রিয়া শুরু করুন 
          </a-button>
        </a-form-item>
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
      <a-card 
        title="ভিজ্যুয়াল পরিদর্শন এবং গ্রেডিং" 
        class="w-full text-6xl"
        style="font-family: 'Hind Siliguri', sans-serif;line-height: 1.5;font-weight: 350;"
        :headStyle="{ backgroundColor: '#088395', color: 'white' }"
      >
           <a-table :pagination="false" :columns="columns"    :data-source="dataSource" bordered
           
           style="font-family: 'Hind Siliguri', sans-serif;"
           >
            
           </a-table> 
      </a-card>
    </a-col>
  </a-row>
</template>

<style scoped>
/* Add any additional custom styles here */
</style>
