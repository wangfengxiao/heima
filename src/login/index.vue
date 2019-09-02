<template>
  <div class="login">

  <el-card class="login-card">

    <div class="logo">
      <img src="../assets/logo_index.png" alt="">
    </div>
     <el-form :model="loginForm" :rules='rules' >
     <el-form-item prop="moblie" >
       <el-input placeholder="请输入手机号" v-model="loginForm.moblie"></el-input>
      
     </el-form-item>

     <el-form-item prop='code'>
       <el-input placeholder="请输人验证码" v-model="loginForm.code" style='width:200px'></el-input>
        <el-button style="float:right;width:100px">发送验证码</el-button>
     </el-form-item>

     <el-form-item prop="check">
       <el-checkbox  v-model="loginForm.check">
         我已阅读并同意用户协议和隐私条款
       </el-checkbox>
     </el-form-item>

     <el-form-item>
       <el-button  style="width:100%">
         登录
       </el-button>
     </el-form-item>
    
   </el-form>
  </el-card>

  </div>
</template>

<script>
export default {
  data(){
       let validator = function(rules,value,callback){
       if(value) {
        callback();
       }else {
         callback(new Error('你必须无条件同意，否侧无法注册'))

       }
     }
  
    return{
      loginForm :{
        moblie:'',
        code:'',
        check: ''

      },
       rules:{
      moblie:[
        {required:true,message:'请输入手机号'},
        {pattern:' /^1[3456789]\d{9}$/',message:"手机号格式错误"}
      
      ],
     code:[
        {required:true,message:'请输入验证码'},
        {pattern:'/^\d{6}$/',message:'验证码格式不正确'}
      
      ],
      check: [
        {validator,
        }
      
      ]
    }

      
    }
  },
  
}
</script>

<style lang=less   scoped> 

       .login {
          background: url('../assets/login_bg.jpg');
          height:100vh;
          background-size:cover;
            display: flex;
         justify-content: center;
         align-items: center;

        
       .login-card {
         width: 400px;
         height: 350px;
         .logo {
           text-align: center;
           .logo img {
           height: 40px;
           
           
         }
         }

         
       }
         

  
       }
</style>