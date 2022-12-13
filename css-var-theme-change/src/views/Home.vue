<template>
  <div class="Home">
    <header class="header">
      <div class="theme-change" id="theme-change"></div>
    </header>
  </div>
</template>

<script setup>
  
</script>

<style lang="scss" scoped>
.Home {
  width: 100vw;
  height: 100vh;
  position: relative;
  background-color: var(--Home-bg-color);
  .header {
    width: calc(100% - 160px);
    padding: 24px 80px;
    position: absolute;
    top: 0;
    left: 0;
    background-color: var(--Home-header-bg-color);
  }
}
</style>