<template>
    <div>
      <!-- 通过$store.state.user 可以获得登陆时记录的用户 -->
      <el-row>
        <el-col :span="6" :offset="18">
          <el-button type="success" class="userIcon">{{$store.state.user.name}}</el-button>
          <el-button type="primary" @click="onLogout" round class="signout">注销</el-button>
        </el-col>
      </el-row>

    </div>
</template>

<script>
  import { mapActions } from 'vuex'
  import ElCol from 'element-ui/packages/col/src/col'

  export default {
    components: {ElCol},
    methods: {
      // 从store.actions中引入方法
      ...mapActions(['logOut', 'loginFail']),
      onLogout: function () {
        this.logOut() // 退出登陆，将user重置为空
        this.loginFail()  // 设置isLogging 为false
      }
    }
  }
</script>

<style>

</style>
