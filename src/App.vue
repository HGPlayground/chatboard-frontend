<template>
  <div id="app">
    <div id="app-header">
      <n-layout>
        <n-layout-header>
          <a href="/" id="brand-link" class="brand-link"> ChatBoard </a>
          <n-menu mode="horizontal" :options="menuOptions"/>
        </n-layout-header>
      </n-layout>
    </div>
    <div id="app-container">
      <router-view />
    </div>
  </div>
</template>

<script>
import {defineComponent, ref} from 'vue'

const menuOptions = [
  {
    label: '匿名板',
    key: 'menu-index',
    disabled: false,
  },
  {
    label: '关于',
    key: 'menu-about',
    disabled: false,
  },
  {
    label: '喂食(不可以！)',
    key: 'menu-feed',
    disabled: true,
  }
]

export default defineComponent({
  setup() {
    return {
      activeKey: ref(null),
      menuOptions
    }
  },
  name: "App"
})
</script>

<style>
#app-container {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#app-header {
  width: 100%;
  height: 40px;
  display: grid;
  overflow: hidden;
  padding: 8px 16px;
  border-bottom: 1px solid #e7e7e7;
}

.brand-link {
  font-size: 20px;
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}
</style>
