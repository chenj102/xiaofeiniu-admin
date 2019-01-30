<template>
  <div id="app">
    <!--
    <h3>{{1000 | date}}</h3>
    <h3>{{1000 | datetime}}</h3>
    <h3>{{1000 | currency}}</h3>
    <div id="nav">
      <router-link to="/">Home</router-link> 
      <router-link to="/about">About</router-link>
    </div>-->
    <router-view/>
    <h4>全局配置：{{$store.state.globalSettings}}</h4>
  </div>
</template>

<script>
export default {
  mounted() {
    //当前组件挂载完成后需要异步请求全局配置数据
    var url=this.$store.state.globalSettings.apiUrl+'/admin/settings';
    this.$axios.get(url).then((res)=>{
      // console.log(res.data);
      this.$store.commit('setGlobalSettings',res.data)
    }).catch((err)=>{
      console.log(err);
    })
  }
}
</script>

<style lang="scss">
#app {
  color: #303133;
  font-family:"Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
