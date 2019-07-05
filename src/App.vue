<template>
  <div id="login">
    <form action="">
      <label for="id">用户名</label>
      <input type="text" v-model.trim="loginData.id" name="id">
      <label for="userPassword">密码</label>
      <input type="password" v-model.trim="loginData.userPassword" name="userPassword">
      <input type="button" value="登陆" @click="doLogin">
    </form>
  </div>
</template>

<script>
import utils from "@/utils/utils"
export default {
  name:'login',
  data () {
    return {
      loginData:{
        id:"",
        userPassword:""
      }
    }
  },
  methods:{
    doLogin(){
      let success=(response)=>{
        alert(response.data.msg);
      }
      utils.axiosMethod({
        method:"POST",
        url:"/loginPage",
        data:this.loginData,
        callback:success
      })
    }
  }
}
</script>
