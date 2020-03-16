<template>
  <div class="login">
    <div class="leftbox">
      <div class="title">
        <img
          class="titleimg"
          src="../../assets/mlogo.png"
          alt=""
        >
        <span class="titlename">黑马面面</span>
        <span class="titleline"></span>
        <span class="titlelogin">用户登录</span>
      </div>
      <el-form
        ref="form"
        :model="form"
        :rules='rules'
      >
        <el-form-item>
          <el-input
            v-model="form.phone"
            placeholder="请输入手机号"
            prefix-icon="el-icon-user"
          ></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input
            v-model="form.password"
            placeholder="请输入密码"
            prefix-icon="el-icon-lock"
            type="password"
          ></el-input>
        </el-form-item>
        <el-form-item prop="logincode">
          <el-row>
            <el-col :span="18">
              <el-input
                v-model="form.logincode"
                placeholder="请输入验证码"
                prefix-icon="el-icon-key"
              ></el-input>
            </el-col>
            <el-col :span="6"><img
                src="../../assets/login_captcha.png"
                alt=""
                class="loginCode"
              ></el-col>
          </el-row>
        </el-form-item>
        <el-form-item
          class="checkBox"
          prop="isChecked"
        >
          <el-checkbox-group v-model="form.isChecked">
            <el-checkbox
              class="checkBox"
              name="type"
            >我已阅读并同意<el-link type="primary">用户协议</el-link>和<el-link type="primary">隐私条款</el-link>
            </el-checkbox>
          </el-checkbox-group>
        </el-form-item>
        <el-form-item>
          <el-button
            type="primary"
            @click="onSubmit"
          >登录</el-button>
        </el-form-item>
        <el-form-item>
          <el-button
            type="primary"
            @click="onRegister"
          >注册</el-button>
        </el-form-item>
      </el-form>
    </div>

    <img
      class="rightimg"
      src="../../assets/login_banner_ele.png"
      alt=""
    >

    <register ref="register"></register>
  </div>
</template>

<script>
import register from "./components/register";
export default {
  data() {
    return {
      form: {
        phone: "",
        password: "",
        logincode: "",
        isChecked: []
      },
      rules: {
        password: [
          { required: true, message: "密码不能为空", trigger: "blur" },
          { min: 5, max: 10, message: "长度在 5 到 10 个字符", trigger: "blur" }
        ],
        logincode: [
          { required: true, message: "验证码不能为空", trigger: "blur" },
          { min: 4, max: 4, message: "验证码长度应该为4", trigger: "blur" }
        ],
        isChecked: [
          {
            type: "array",
            required: true,
            message: "请先仔细阅读用户协议和隐私条款",
            trigger: "change"
          }
        ]
      }
    };
  },
  methods: {
    onSubmit() {
      this.$refs.form.validate(valid => {
        if (valid) {
          this.$message({
            message: "登录成功",
            type: "success"
          });
        } else {
          this.$message.error("fail");
        }
      });
    },
    onRegister() {
      this.$refs.register.dialogFormVisible = true
    }
  },
  components: {
    register
  }
};
</script>

<style lang="less">
.login {
  height: 100%;
  background: linear-gradient(
    225deg,
    rgba(20, 147, 250, 1),
    rgba(1, 198, 250, 1)
  );
  display: flex;
  justify-content: space-around;
  align-items: center;

  .leftbox {
    width: 478px;
    height: 550px;
    background: rgba(245, 245, 245, 1);
    padding: 48px 42px 86px;
    box-sizing: border-box;

    .title {
      display: flex;
      align-items: center;

      .titleimg {
        width: 22px;
        height: 17px;
      }

      .titlename {
        font-size: 24px;
        font-family: SourceHanSansCN;
        font-weight: 400;
        color: rgba(12, 12, 12, 1);
        margin-left: 16px;
        margin-right: 14px;
      }

      .titleline {
        width: 1px;
        height: 28px;
        background: rgba(199, 199, 199, 1);
        margin-right: 12px;
      }

      .titlelogin {
        font-size: 22px;
        font-family: PingFangSC;
        font-weight: 400;
        color: rgba(12, 12, 12, 1);
      }
    }

    form {
      margin-top: 29px;

      .loginCode {
        width: 100%;
        height: 40px;
      }

      .checkBox {
        .el-form-item__content {
          line-height: 20px;
        }
      }

      button {
        width: 100%;
      }
    }
  }

  .rightimg {
    width: 633px;
    height: 435px;
  }
}
</style>