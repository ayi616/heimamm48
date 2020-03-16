<template>
  <div class="app">
    <el-input
      placeholder="请输入手机号"
      prefix-icon="el-icon-user"
      v-model="input1"
    > </el-input>
    <el-input
      placeholder="请输入密码"
      prefix-icon="el-icon-lock"
      v-model="input1"
    > </el-input>
    <el-input
      placeholder="请输入验证码"
      prefix-icon="el-icon-key"
      v-model="input1"
    >
    </el-input>
      <el-link type="primary">主要链接</el-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input1: ""
    };
  }
};
</script>

<style>
</style> 