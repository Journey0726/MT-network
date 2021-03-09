<template>
  <div class="page-register">
    <article class="header">
      <header>
        <a href="/" class="site-logo" />
        <span class="login"
          ><em class="bold">已有美团账号?</em>
          <a href="/login">
            <el-button type="primary" size="small">登录</el-button>
          </a>
        </span>
      </header>
    </article>
    <section>
      <el-form
        :model="ruleForm"
        status-icon
        :rules="rules"
        ref="ruleForm"
        label-width="100px"
      >
        <el-form-item label="昵称" prop="name">
          <el-input
            v-model="ruleForm.name"
          ></el-input>
        </el-form-item>
        <el-form-item label="邮箱" prop="email">
          <el-input
            v-model="ruleForm.email"
          ></el-input>
          <el-button size="mini" round @click="sendMessage">发送验证码</el-button>
          <span class="status">{{statusMsg}}</span>
        </el-form-item>
        <el-form-item label="验证码" prop="code">
          <el-input v-model="ruleForm.code" maxlength="4"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="pwd">
          <el-input
            v-model="ruleForm.pwd" type="password"
          ></el-input>
        </el-form-item>
        <el-form-item label="确认密码" prop="cpwd">
          <el-input
            v-model="ruleForm.cpwd" type="password"
          ></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="register">同意协议并注册</el-button>
          <div class="error">{{error}}</div>
        </el-form-item>
        <el-form-item>
          <a href="http://www.meituan.com.about/terms" target="_blank">《美团网用户协议》</a>
        </el-form-item>
          </el-form>
    </section>
  </div>
</template>

<script>
export default {
  layout: "blank",
  data(){
    return{
      ruleForm:{
        name:'ddd',
        code:'dddd',
        pwd:'ddddd',
        cpwd:"ddddd",
        email:'1111555255@qq.com'
      },
      rules:{
        name:[{required:true,type:'string',message:'请输入昵称',trigger:'blur'}],
        email:[{required:true,type:'email',message:'请输入邮箱',trigger:'blur'}],
        pwd:[{required:true,message:'请输入密码',trigger:'blur'}],
        cpwd:[{required:true,message:'确认密码',trigger:'blur'},{
          validator:(rule,value,callpack)=>{
            if(value==''){
              callpack(new Error('请再次输入密码'))
            }
            else if(value !== this.ruleForm.pwd){
              callpack(new Error('两次输入密码不一致'))
            }
            else callpack()
          },trigger:'blur'
        },],

      },
      statusMsg:'',
      error:''
    }
  },
  methods:{
    sendMessage(){

    },
    register(){
      this.$router.push('/register')
    }
  }
};
</script>

<style lang='scss'>
@import "@/assets/css/register/index.scss";
</style>