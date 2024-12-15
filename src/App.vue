<script setup lang="ts">
import TheHeader from './components/TheHeader.vue'
import TheBanner from './components/TheBanner.vue'
import ProductFeatures from './components/ProductFeatures.vue'
import Services from './components/Services.vue'
import CustomerCases from './components/CustomerCases.vue'
import TheFooter from './components/TheFooter.vue'
</script>

<template>
  <div class="app">
    <!-- 头部导航 -->
    <TheHeader />
    
    <!-- Banner区域 -->
    <TheBanner />

    <!-- 产品功能介绍 -->
    <section id="features" class="section">
      <ProductFeatures />
    </section>

    <!-- 更多服务 -->
    <section id="services" class="section bg-gray">
      <Services />
    </section>

    <!-- 客户案例 -->
    <section id="cases" class="section">
      <CustomerCases />
    </section>

    <!-- 页脚 -->
    <TheFooter />
  </div>
</template>

<style scoped>
.app {
  width: 100%;
  min-height: 100vh;
  padding-top: 60px;
  scroll-behavior: smooth;
}

.section {
  padding: 80px 0;
  width: 100%;
}

.bg-gray {
  background-color: #f5f5f5;
}
</style>