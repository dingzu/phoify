<template>
  <div class="container">
    <h2 class="section-title">客户案例</h2>
    <div class="cases-grid">
      <div v-for="(case_item, index) in cases" 
           :key="index" 
           class="case-item">
        <img :src="case_item.image" :alt="case_item.title">
        <h3>{{ case_item.title }}</h3>
        <p>{{ case_item.description }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

interface Case {
  title: string;
  description: string;
  image: string;
}

export default defineComponent({
  name: 'CustomerCases',
  
  data() {
    return {
      cases: [
        {
          title: '案例一',
          description: '这是第一个成功案例的详细描述...',
          image: new URL('@/assets/vue.svg', import.meta.url).href
        },
        {
          title: '案例二',
          description: '这是第二个成功案例的详细描述...',
          image: new URL('@/assets/vue.svg', import.meta.url).href
        },
        // Add more cases as needed
      ] as Case[]
    }
  }
})
</script>

<style scoped>
.container {
  padding: 2rem;
}

.section-title {
  text-align: center;
  margin-bottom: 2rem;
}

.cases-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.case-item {
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.case-item:hover {
  transform: translateY(-5px);
}

.case-item img {
  width: 100%;
  height: auto;
  border-radius: 4px;
  margin-bottom: 1rem;
}

.case-item h3 {
  margin-bottom: 0.5rem;
}

.case-item p {
  color: #666;
  line-height: 1.5;
}
</style>