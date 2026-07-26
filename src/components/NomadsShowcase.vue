<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">编程开发与代码重构实战模板库</h2>
        <p class="showcase-subtitle">精选全栈开发、Bug 诊断与高性能算法场景，点击“一键套用”生成生产级代码</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个代码框架模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次生成</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const emit = defineEmits<{
  (e: 'apply-template', payload: { prompt: string; scenario?: string; techStack?: string }): void;
}>();

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  scenario?: string;
  techStack?: string;
  usageCount: string;
}

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'biancheng-1',
    tag: '前端全栈',
    title: 'Vue3 + TS 大文件切片断点续传组件',
    prompt: '编写一个 Vue3 + TypeScript 大文件分片上传 Hook，支持 SparkMD5 秒传、并发数控制（支持最多 3 个切片同时上传）、失败自动重试 3 次及断点续传。',
    scenario: '全栈代码实现与重构',
    techStack: 'TypeScript/Vue/React',
    usageCount: '68.5k'
  },
  {
    id: 'biancheng-2',
    tag: 'Python后端',
    title: 'FastAPI 异步 JWT 双 Token 无感刷新',
    prompt: '使用 Python FastAPI + SQLAlchemy 2.0 (Async)，实现 Access Token (15分钟) 和 Refresh Token (7天) 的双 Token 无感刷新认证中间件。',
    scenario: 'API接口与架构设计',
    techStack: 'Python/Django/FastAPI',
    usageCount: '52.1k'
  },
  {
    id: 'biancheng-3',
    tag: 'Java企业级',
    title: 'Spring Boot Redis 分布式锁切面注解',
    prompt: '使用 Redisson 封装一个 `@DistributedLock` 自定义 AOP 切面注解，支持锁自动续期、防误删及等待超时安全退出的生产级实现。',
    scenario: '全栈代码实现与重构',
    techStack: 'Java/Spring Boot',
    usageCount: '59.3k'
  },
  {
    id: 'biancheng-4',
    tag: 'Go高并发',
    title: 'Go 语言 WorkerPool 协程池与优雅退出',
    prompt: '用 Go 编写一个泛型 WorkerPool 协程池，支持 Channel 任务队列排队、Context 超时取消、平滑优雅关闭（Graceful Shutdown）与 Panic 捕获。',
    scenario: '算法设计与复杂度优化',
    techStack: 'Go/Microservices',
    usageCount: '44.7k'
  },
  {
    id: 'biancheng-5',
    tag: '数据结构',
    title: 'O(1) 时间复杂度 LRU 缓存算法双向链表',
    prompt: '使用 TypeScript 实现一个真正的 O(1) 查找与更新 LRU (Least Recently Used) 缓存类，利用双向链表 + Map 结构，并附带 Jest 测试用例。',
    scenario: '算法设计与复杂度优化',
    techStack: 'TypeScript/Vue/React',
    usageCount: '41.2k'
  },
  {
    id: 'biancheng-6',
    tag: 'Bug诊断',
    title: '解决 Node.js 内存泄漏与 EventListener 堆栈',
    prompt: '诊断排查：Node.js 服务高并发运行 24 小时后发生 OOM (JavaScript heap out of memory)，定位 EventEmitter 未移除与闭包引用并重构修正。',
    scenario: 'Bug排查与堆栈诊断',
    techStack: 'TypeScript/Vue/React',
    usageCount: '37.8k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    scenario: item.scenario,
    techStack: item.techStack
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>
