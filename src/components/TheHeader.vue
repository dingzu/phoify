<template>
  <header class="header">
    <nav class="nav">
      <img 
        src="../assets/logo.png" 
        alt="Logo" 
        class="logo"
        @click="scrollToTop"
        style="cursor: pointer"
      >
      <div class="nav-links">
        <a @click.prevent="scrollToSection('features')" class="nav-link">小试牛刀</a>
        <a @click.prevent="scrollToSection('services')" class="nav-link">更多服务</a>
        <a @click.prevent="scrollToSection('cases')" class="nav-link">客户案例</a>
      </div>
      <button class="contact-btn" @click="showContactModal = true">
        联系我们
      </button>
    </nav>

    <div v-if="showContactModal" class="modal-overlay" @click="showContactModal = false">
      <div class="modal-content" @click.stop>
        <h2>联系我们</h2>
        <p>电话：123-456-7890</p>
        <p>邮箱：contact@example.com</p>
        <button class="close-btn" @click="showContactModal = false">关闭</button>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const showContactModal = ref(false)

const scrollToSection = (id: string) => {
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ 
      behavior: 'smooth',
      block: 'start'
    })
  }
}

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}
</script>

<style scoped lang="less">
@import '../styles/variables.less';

.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background: @white;
  box-shadow: @box-shadow;
  z-index: @z-index-header;
}

.nav {
  max-width: @max-width;
  height: @header-height;
  margin: 0 auto;
  padding: 0 @spacing-xlarge;
  display: flex;
  justify-content: space-between;
  align-items: center;

  .logo {
    height: 40px;
    width: auto;
  }

  .nav-links {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: @spacing-xlarge;

    .nav-link {
      color: @text-color;
      text-decoration: none;
      font-size: @spacing-base;
      transition: color @transition-duration;
      cursor: pointer;

      &:hover {
        color: @primary-color;
      }
    }
  }

  .contact-btn {
    padding: @spacing-small @spacing-large;
    background-color: @primary-color;
    color: @white;
    border: none;
    border-radius: @border-radius;
    cursor: pointer;
    transition: background-color @transition-duration;

    &:hover {
      background-color: @primary-hover-color;
    }
  }
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(@black, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: @z-index-modal;

  .modal-content {
    background-color: @white;
    padding: @spacing-xlarge;
    border-radius: @border-radius;
    min-width: 300px;
    text-align: center;

    h2 {
      margin-bottom: @spacing-base;
      color: @text-color;
    }

    p {
      margin: @spacing-small 0;
      color: @text-light-color;
    }

    .close-btn {
      margin-top: @spacing-large;
      padding: @spacing-small @spacing-large;
      background-color: @primary-color;
      color: @white;
      border: none;
      border-radius: @border-radius;
      cursor: pointer;
      transition: background-color @transition-duration;

      &:hover {
        background-color: @primary-hover-color;
      }
    }
  }
}
</style>