<template>
  <div class="container">
    <h2 class="section-title">产品功能</h2>
    
    <div class="features-nav">
      <div 
        v-for="(tab, index) in tabs" 
        :key="index"
        :class="['nav-item', { active: currentTab === index }]"
        @click="switchTab(index)"
      >
        {{ tab.name }}
      </div>
    </div>

    <div class="feature-card">
      <Transition name="fade" mode="out-in">
        <component :is="currentComponent" :key="currentTab"></component>
      </Transition>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import ImageGeneration from './features/ImageGeneration.vue'
import ImageMatting from './features/ImageMatting.vue'
import BatchBackground from './features/BatchBackground.vue'
import MarketingPoster from './features/MarketingPoster.vue'

const currentTab = ref(0)
const tabs = [
  { name: '智能生图', component: ImageGeneration },
  { name: '智能抠图', component: ImageMatting },
  { name: '批量换背景', component: BatchBackground },
  { name: '营销海报生成', component: MarketingPoster }
]

const currentComponent = computed(() => {
  return tabs[currentTab.value].component
})

const switchTab = (index: number) => {
  currentTab.value = index
}
</script>

<style scoped lang="less">
@import '../styles/variables.less';

.container {
  padding: 40px 0;
  
  .section-title {
    text-align: center;
    margin-bottom: @spacing-xlarge;
    font-size: 24px;
    color: @text-color;
  }

  .features-nav {
    display: flex;
    justify-content: center;
    gap: @spacing-xlarge;
    margin-bottom: @spacing-xlarge;

    .nav-item {
      padding: @spacing-small @spacing-large;
      cursor: pointer;
      border-radius: @border-radius;
      transition: all @transition-duration;
      color: @text-color;
      
      &:hover {
        background-color: #f5f5f5;
      }
      
      &.active {
        background-color: @primary-color;
        color: @white;
      }
    }
  }

  .feature-card {
    max-width: @max-width;
    margin: 0 auto;
    min-height: 400px;
    background: @white;
    border-radius: @border-radius;
    box-shadow: @box-shadow;
    padding: @spacing-xlarge;
    position: relative;
  }

  // 添加过渡动画样式
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.3s ease, transform 0.3s ease;
  }

  .fade-enter-from {
    opacity: 0;
    transform: translateY(20px);
  }

  .fade-leave-to {
    opacity: 0;
    transform: translateY(-20px);
  }
}
</style>