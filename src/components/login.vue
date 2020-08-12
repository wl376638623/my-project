<template>
 <div style="width: 60%;margin: auto;">
   <div class="login-wrap">
     <el-form class="login-container">
       <h1 class="title">用户登录</h1>
       <el-form-item label="">
         <el-input type="text" autocomplete="off" placeholder="请输入手机号"></el-input>
       </el-form-item>
       <el-form-item label="">
         <el-input type="password" autocomplete="off" placeholder="请输入密码"></el-input>
       </el-form-item>
       <el-form-item>
         <el-button type="primary" style="width: 100%;" @click="tijiao">确定</el-button>
       </el-form-item>
       <el-row style="text-align: center; margin-top: -10px;;">
         <el-link type="primary">忘记密码</el-link>
         <el-link type="primary" @click="doRegister">用户注册</el-link>
       </el-row>
     </el-form>
   </div>
 </div>
</template>

<script>
    export default {
        name: "login",
      data() {
       return{

       }
      },
        methods: {
        // <!--进入注册页-->
          doRegister() {
          this.$router.push({
            path: "/register"
          });
        },
          tijiao() {
            this.$router.push({
              path: "/news_list"
            });
          }
      }
    }
</script>

<style scoped>

</style>
