<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[代码生成完成]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  { text: '用户 138****0192 完成了 Vue3 + TS 大文件切片断点续传组件开发' },
  { text: '用户 177****8810 诊断修复了 Python asyncio 协程死锁与内存泄漏问题' },
  { text: '用户 189****3321 实现了 Java Spring Boot 动态数据源多租户切面' },
  { text: '用户 131****5643 优化了 Go 语言高并发无锁队列算法实现 (O(1)复杂度)' },
  { text: '用户 153****7780 生成了 React 声明式虚拟滚动列表及 Jest 单测' },
]);
</script>
