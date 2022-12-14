<template>
  <div class="Home">
    <header class="header">
      <div class="theme-change" id="theme-change">
        <div class="change" @click="changeThemes(theme)">换肤</div>
      </div>
    </header>
  </div>
</template>

<script setup>
let theme = "drak";
/**
 * 主题切换函数
 * @param {string} theme - 主题名称，默认值：default
 * @return {string} 主题名称
 */
const changeThemes = ($theme = "default") => {
  theme = $theme === "default" ? "drak" : "default";
  const link = createLink();
  console.log(theme, link);
  link.href = `src/themes/${$theme}.css`;
  return $theme;
};

/**
 * 创建一个link元素用于替换原本的link，以此来引入新的CSS资源
 */
const createLink = (() => {
  let link = null;
  return () => {
    // 如果之前已经创建过link元素，那么就不添加新的link元素了
    // 直接返回原本的link元素对href进行赋值即可，避免重复添加过多的link元素
    if (link) {
      return link;
    }
    // 创建一个link元素
    link = document.createElement("link");
    // 设置link元素的 rel、type属性
    link.rel = "stylesheet";
    link.type = "text/css";
    // 向页面头部添加 link 元素
    document.querySelector("head").appendChild(link);
    return link;
  };
})();
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
    display: flex;
    align-items: center;
    justify-content: flex-end;

    .change {
      padding: 6px 48px;
      border-radius: 50px;
      border: 1px solid var(--Home-header-changeButton-borderColor);
      color: var(--Home-header-changeButton-fontColor);
      cursor: pointer;
      transition: all 0.15s ease-in;
      &:hover {
        padding: 6px 60px;
        border: 1px solid var(--Home-header-changeButton-borderColor-hover);
        color: var(--Home-header-changeButton-fontColor-hover);
        background-color: var(--Home-header-changeButton-bgColor-hover);
      }
    }
  }
}
</style>