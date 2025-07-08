<template>
  <div class="flex h-screen font-sans text-gray-800">
    <!-- Sidebar -->
    <aside class="w-64 bg-gray-100 border-r p-6">
      <h2 class="text-xl font-semibold mb-4">求职经历</h2>
      <ul class="space-y-2">
        <li
          v-for="(job, index) in jobs"
          :key="job.id"
          @click="selectJob(index)"
          :class="[
            'cursor-pointer px-3 py-2 rounded-lg transition',
            selected === index ? 'bg-blue-500 text-white' : 'hover:bg-gray-200'
          ]"
        >
          {{ job.title }}
        </li>
      </ul>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 p-10 overflow-y-auto">
      <div v-if="selected === null" class="text-gray-400 text-center mt-40 text-lg">
        请选择左侧的一个职位以查看总结内容。
      </div>
      <div v-else class="max-w-3xl">
        <h1 class="text-2xl font-bold mb-6">{{ jobs[selected].title }}</h1>
        <div v-html="jobs[selected].content" class="prose max-w-none"></div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const selected = ref(null)

const jobs = ref([
  {
    id: 't4t',
    title: 'T4T Full Stack Internship',
    content: `
      <h3>公司背景</h3>
      <p>T4T 是一个非营利组织...</p>
      <h3>项目内容</h3>
      <ul><li>使用 FastAPI 构建后台</li><li>Firebase 实现权限控制</li></ul>
    `
  },
  {
    id: 'kuaishou',
    title: '快手 Java 一面',
    content: `
      <h3>技术问题</h3>
      <ul><li>Redis 为什么线程安全？</li><li>JVM 内存结构？</li></ul>
    `
  }
])
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

html {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
}
</style>