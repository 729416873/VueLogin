<template>

<div >
  <el-container>
    <el-aside width="200px">侧边栏</el-aside>
    <el-container>
      <el-header>头部</el-header>
      <el-main>中心内容</el-main>
    </el-container>
  </el-container>

</div>

</template>

<script>
    export default {
        name: "HelloWorld",
        data(){
          return {
            msg:'欢迎每次事实上'
          }
        }
    }
</script>

<!-- scoped 只可被当前文件使用 -->
<style scoped>
  .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }

  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }

  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }

  body > .el-container {
    margin-bottom: 40px;
  }

  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }

  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
</style>
