<template>
    <div class="login_content">
        <div class="login_box">
            <div class="avatar_box">
                <img src="../assets/logo.png" alt="">
            </div>
            <el-form ref="loginFormRef" :model="loginForm" :rules="loginFormRules" label-width="0px" class="login_form">
                <el-form-item prop="username">
                    <el-input v-model="loginForm.username" prefix-icon="iconfont icon-user"></el-input>
                </el-form-item>
                <el-form-item prop="password">
                    <el-input v-model="loginForm.password" prefix-icon="iconfont icon-password" type="password"></el-input>
                </el-form-item>
                <el-form-item class="btns">
                    <el-button type="primary" @click="login">登录</el-button>
                    <el-button type="info" @click="resetLoginForm">重置</el-button>
                </el-form-item>
            </el-form>
        </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      loginForm: {
        username: '',
        password: ''
      },
      loginFormRules: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { min: 6, max: 15, message: '长度在 6 到 15 个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    resetLoginForm () {
      this.$refs.loginFormRef.resetFields()
      // Object.keys(this.loginForm).forEach(key => this.loginForm[key] === '')
      for (var key in this.loginForm) {
        this.loginForm[key] = ''
      }
    },
    login () {
      this.$refs.loginFormRef.validate(valid => {
        if (valid) {
          console.log(valid)
        }
      })
    }
  }
}
</script>
<style lang="scss" scope>
    .login_content {
        background-color: #2b4b6b;
        height: 100%;
        .login_box {
            width: 450px;
            height: 300px;
            background-color: aliceblue;
            border-radius: 5px;
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%,-50%);
            .avatar_box{
                width: 130px;
                height: 130px;
                border-radius: 50%;
                border: 1px solid #eee;
                padding: 10px;
                position: absolute;
                left: 50%;
                transform: translate(-50%,-50%);
                background-color: #fff;
                img{
                    width: 100%;
                    height: 100%;
                    border-radius: 50%;
                    background-color: #eee;
                }
            }
        }
        .login_form{
            position: absolute;
            bottom: 0;
            box-sizing: border-box;
            width: 100%;
            padding: 0 20px;
        }
        .btns{
            display: flex;
            justify-content: flex-end;
        }
    }
</style>
