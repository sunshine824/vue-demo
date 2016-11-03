<template>
  <!--<form-->
    <!--role="search"-->
    <!--class="navbar-form navbar-right"-->
    <!--@submit.prevent="handleLogin">-->
    <!--<div class="form-group">-->
      <!--<input-->
        <!--required-->
        <!--type="text"-->
        <!--class="form-control"-->
        <!--placeholder="请输入您的用户名"-->
        <!--v-model="username"/>-->
    <!--</div>-->
  <!--</form>-->
  <ul class="nav navbar-nav navbar-right">
    <li class="dropdown">
      <a href="#" class="dropdown-toggle" data-toggle="dropdown">会员登录<span class="caret"></span></a>
      <ul class="dropdown-menu" role="menu">
        <li>
          <a
             href="#"
             v-link="'/login'">
             登录
          </a>
        </li>
        <li class="divider"></li>
        <li>
          <a
             href="#"
             v-link="'/register'">
             注册
          </a>
        </li>
      </ul>
    </li>
  </ul>
    <!--<button-->
            <!--type="submit"-->
            <!--class="btn btn-success">-->
      <!--注册-->
    <!--</button>-->
    <!--<button-->
      <!--type="submit"-->
      <!--class="btn btn-success">-->
      <!--登录-->
    <!--</button>-->

</template>
<script>
import userService from 'SERVICE/userService'
export default {
  data () {
    return {
      username: '' // v-model 必须设置默认值
    }
  },

  methods: {
    handleLogin () {
      console.info('[LoginForm:XHR] 发送登录请求')
      userService
        .login({ username: this.username })
        .then((userSessData) => {
          console.info('[LoginForm] 登录成功，立即设置 session 到 $root.userData')
          this.$root.userData = userSessData
        })
    }
  }
}
</script>
