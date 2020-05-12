<template>
    <div class="mainbar">
      <a-menu mode="horizontal" :default-selected-keys="['1']">
        <a-menu-item key="1"><a-icon type="bell" />个人提醒</a-menu-item>
        <a-menu-item key="2"><a-icon type="flag" />我的主题</a-menu-item>
        <a-menu-item key="3"><a-icon type="retweet" />我的回复</a-menu-item>
      </a-menu>
    </div>
</template>

<script>
    export default {
        name: "mainpageBar.vue"
    }
</script>

<style scoped>
.mainbar {
  width: 67%;
  margin: 15px auto 0;
}
</style>
