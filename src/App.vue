<template>
<div class="app">
  <!-- 验证router是否挂在吃呢彀给你可以在App.vue中添加一个<router-link to="/">我是a链接</router-link>
    如果标签解析为一个超链接，则挂载成功，否则失败
    router-link必须有一个to属性
   -->
  <!-- <router-link to="/">ayi</router-link> -->
  <router-view></router-view>
</div>
</template>

<script>

export default {
  name: 'App',
  components: {
  }
}
</script>

<style>

</style>
