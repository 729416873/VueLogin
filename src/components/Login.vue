<template>
  <div class="login_container">
    <!--    登陆模块中间的图标-->
    <div class="login_box">
      <div class="avatar_box">
        <img  src="../assets/logo.png" alt="">
      </div>
      <!--     登陆表单区域-->
      <el-form ref="loginformref" :model="loginForm"  label-width="0px" class="login_form">

        <el-form-item prop="name">
          <el-input v-model="loginForm.name"  placeholder="请输入用户名"
                    prefix-icon="el-icon-user-solid"></el-input>
        </el-form-item>

        <!--        prop="password"为了重置成功  表单域 model 字段，
        在使用 validate、resetFields 方法的情况下，该属性是必填的
        https://www.cnblogs.com/chr506029589/p/11290161.html -->
        <el-form-item  prop="password">
          <el-input v-model="loginForm.password" placeholder="请输入密码"
                    prefix-icon="el-icon-lock"  type="password"></el-input>
        </el-form-item>

        <el-form-item class="btns">
          <el-button type="primary" @click="login">登录</el-button>
          <el-button type="info" @click="resetLoginForm">重置</el-button>
        </el-form-item >

      </el-form>
      <!--      button-->

    </div>
  </div>
</template>

<script>
  export default {
    name: "Login",
    data(){
      return{
        //这是登录表单的数据绑定对象
        loginForm:{
          name:"admin",
          password:"123456"
        }
      }
    },
    methods:{
      resetLoginForm(){
        // console.log(this)
        this.$refs.loginformref.resetFields()
      },
      login(){
        this.$refs.loginformref.validate(async valid=>{
          // console.log(valid)
          if (!valid)return;
          // const result = await this.$http.post("/image/login",this.loginForm)
          const {data:res} = await this.$http.post("/image/loginData",this.loginForm);

          console.log(res);
        });
      },
      getlunbo() {
        this.$http.get('/image/test')
          .then(function (response) {
            console.log(response);
          })
          .catch(function (error) {
            console.log(error);
          });

      }
    }
  }
</script>

<style lang="less" scoped>
  /*全局背景*/
  .login_container{
    background-color: #2b4b6b;
    height: 100%;
  }
  /*登陆模块*/
  .login_box{
    width: 450px;
    height: 300px;
    background-color: #fff;
    border-radius:3px;
    position: absolute;
    left: 50%;
    top: 50%;
    -webkit-transform: translate(-50%,-50%);
    -moz-transform: translate(-50%,-50%);
    transform: translate(-50%,-50%);
    /*图标*/
    .avatar_box{
      height: 130px;
      width: 130px;
      border :1px solid #eee;
      border-radius: 50%;
      padding: 10px;
      //加阴影，向外扩散10-px
      box-shadow: 0 0 10px #ddd;
      /*居中*/
      position: absolute;
      left:50% ;
      transform: translate(-50%,-50%);
      background-color: #fff;
      img{
        width: 100%;
        height: 100%;
        border-radius: 50%;
        border :1px solid #eee;
        background-color: #eee;
      }
    }
  }

  .login_form{
    position: absolute;
    bottom: 0px;
    width: 100%;
    padding: 20px;
    box-sizing: border-box;
  }
  .btns{
    display:flex;
    justify-content: flex-end;
    /*  justify-content: center; 居中排列
  justify-content: flex-start;  从行首起始位置开始排列
    justify-content: flex-end; 从行尾位置开始排列 */

  }
</style>
