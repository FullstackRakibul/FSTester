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
      <div class="logo" />
      <a-menu v-model:selectedKeys="selectedKeys" mode="inline">
        <a-menu-item key="1">
          <user-outlined />
          <span>User</span>
        </a-menu-item>
        <a-menu-item key="2">
          <video-camera-outlined />
          <span>Camera</span>
        </a-menu-item>
        <a-menu-item key="3">
          <upload-outlined />
          <span>Upload</span>
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
import { ref } from 'vue';
import {
  UserOutlined,
  VideoCameraOutlined,
  UploadOutlined,
} from '@ant-design/icons-vue';
import OperationDashboard from './components/core/OperationDashboard.vue';

const selectedKeys = ref<string[]>(['1']);
const collapsed = ref<boolean>(true);
</script>

<style>
/* Customize the logo section */
.logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.3);
  margin: 16px;
}

/* Apply custom styles for sidebar and layout */
</style>
