<template>
  <el-dialog
    class="reg_dialog"
    title="用户注册"
    :visible.sync="dialogFormVisible"
  >
    <el-form
      :model="form"
      :rules="rules"
      ref="form"
    >
      <el-form-item
        prop="nickname"
        label="昵称"
        :label-width="formLabelWidth"
      >
        <el-input
          v-model="form.nickname"
          autocomplete="off"
        ></el-input>
      </el-form-item>
      <el-form-item
        prop="email"
        label="邮箱"
        :label-width="formLabelWidth"
      >
        <el-input
          v-model="form.email"
          autocomplete="off"
        ></el-input>
      </el-form-item>
      <el-form-item
        prop="tel"
        label="手机"
        :label-width="formLabelWidth"
      >
        <el-input
          v-model="form.tel"
          autocomplete="off"
        ></el-input>
      </el-form-item>
      <el-form-item
        prop="password"
        label="密码"
        :label-width="formLabelWidth"
      >
        <el-input
          v-model="form.password"
          autocomplete="off"
        ></el-input>
      </el-form-item>

      <el-form-item
        prop="code"
        label="图形码"
        :label-width="formLabelWidth"
      >
        <el-row>
          <el-col :span="18">
            <el-input
              v-model="form.code"
              autocomplete="off"
            ></el-input>
          </el-col>
          <el-col
            :span="6"
            class="code_left"
          ><img
              class="img_right"
              src="../../../assets/login_captcha.png"
              alt=""
            ></el-col>
        </el-row>
      </el-form-item>

      <el-form-item
        prop="logincode"
        label="验证码"
        :label-width="formLabelWidth"
      >
        <el-row>
          <el-col :span="18">
            <el-input
              v-model="form.logincode"
              autocomplete="off"
            ></el-input>
          </el-col>
          <el-col
            :span="6"
            class="code_left"
          >
            <el-button class="img_right">获取用户验证码</el-button>
          </el-col>
        </el-row>

      </el-form-item>
    </el-form>
    <div
      slot="footer"
      class="dialog-footer"
    >
      <el-button @click="dialogFormVisible = false">取 消</el-button>
      <el-button
        type="primary"
        @click="onSubmit"
      >确 定</el-button>
    </div>
  </el-dialog>
</template>

<script>
export default {
  data() {
    return {
      dialogFormVisible: false,
      form: {
        nickname: "",
        email: "",
        tel: "",
        password: "",
        code: "",
        logincode: ""
      },
      rules: {
        nickname: [
          { required: true, message: "昵称不能为空", trigger: "blur" },
          { min: 5, max: 10, message: "长度在 5 到 10 个字符", trigger: "blur" }
        ],
        email: [{ required: true, message: "邮箱不能为空", trigger: "blur" }],
        tel: [
          { required: true, message: "手机不能为空", trigger: "blur" },
          { min: 11, max: 11, message: "手机号码长度为11", trigger: "blur" }
        ],
        password: [
          { required: true, message: "密码不能为空", trigger: "blur" },
          { min: 5, max: 10, message: "长度在 5 到 10 个字符", trigger: "blur" }
        ],
        code: [
          { required: true, message: "图形码不能为空", trigger: "blur" },
          { min: 4, max: 4, message: "图形长度应该为4", trigger: "blur" }
        ],
        logincode: [
          { required: true, message: "验证码不能为空", trigger: "blur" },
          { min: 6, max: 6, message: "验证码长度应该为6", trigger: "blur" }
        ]
      },
      formLabelWidth: "67px"
    };
  },
  methods: {
    onSubmit() {
      this.$refs.form.validate(valid => {
        if (valid) {
          this.$message({
            message: "验证通过",
            type: "success"
          });
        } else {
          this.$message.error("验证不通过");
        }
      });
    }
  }
};
</script>

<style lang="less">
.reg_dialog {
  .el-dialog__header {
    height: 53px;
    line-height: 53px;
    padding: 0;
    text-align: center;
    background: linear-gradient(to right, #0dc1ef, #1394fc);

    .el-dialog__title {
      color: #ffffff;
    }
  }

  .code_left {
    height: 41px;
    text-align: right;

    .img_right {
      width: 143px;
      height: 41px;
    }
  }

  .dialog-footer {
    text-align: center;
  }
}
</style>