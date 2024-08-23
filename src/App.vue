<template>
  <a-layout style="min-height: 100vh;">
    <a-layout-sider
      v-model:collapsed="collapsed"
      collapsible
      :trigger="null"
      :collapsed-width="80"
      width="200"
     style="background-color: white;"
    >
      <div class="logo" >
        <a-image
        :width="45"
        src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTWm2-J1ZpsiXxwlb4EV6Mwch_Ikeb8joz8Sw&s"
        />
      </div>
      <a-menu v-model:selectedKeys="selectedKeys" mode="inline">
        <a-menu-item key="1">
          <DotChartOutlined />
          <span>checking and evaluation</span>
        </a-menu-item>
        <a-menu-item key="2">
          <ExperimentOutlined />
          <span>Create Inspection</span>
        </a-menu-item>
        <a-menu-item key="3">
          <AuditOutlined />
          <span>Process Checking</span>
        </a-menu-item>
        <a-menu-item key="4">
          <ReconciliationOutlined />
          <span>Quality Checking</span>
        </a-menu-item>
      </a-menu>
    </a-layout-sider>
    <a-layout>
      <a-layout-content
        :style="{ margin: '24px 16px', padding: '12px', background: '#fff', overflow: 'auto'}"
      >
        <div style="padding: 10px; min-height:fit-content;">
          <OperationDashboard/>
        </div>
      </a-layout-content>
    </a-layout>
  </a-layout>
</template>

<script lang="ts" setup>
import './app.less'
import { ref } from 'vue';
import {
  ExperimentOutlined,
  AuditOutlined,
  ReconciliationOutlined,
  DotChartOutlined
} from '@ant-design/icons-vue';
import OperationDashboard from './components/core/OperationDashboard.vue';

const selectedKeys = ref<string[]>(['1']);
const collapsed = ref<boolean>(true);
</script>

<style scoped>

/* Customize the logo section */
.logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.3);
  margin: 16px;
}

/* Apply custom styles for sidebar and layout */
</style>
