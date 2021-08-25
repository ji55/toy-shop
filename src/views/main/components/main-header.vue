<template>
  <div>
    <el-row class="main-header" :gutter="20">
      <el-col :offset="9" :span="5"><div class="title">Toy</div></el-col>
      <el-col :xs="2" :sm="3" :md="7"></el-col>
      <el-col :xs="8" :sm="7" :md="3" class="header-icon">
        <a><i class="el-icon-search"></i></a>
        <a><i class="el-icon-shopping-cart-2"></i></a>
      </el-col>
    </el-row>
    <el-row class="main-menu" :gutter="20">
      <el-col :xs="9" :sm="6"></el-col>
      <el-col :xs="10" :sm="3">유아완구</el-col>
      <el-col :xs="9" :sm="0"></el-col>
      <el-col :xs="10" :sm="3">키덜트존</el-col>
      <el-col :xs="9" :sm="0"></el-col>
      <el-col :xs="10" :sm="3">기획전</el-col>
      <el-col :xs="9" :sm="0"></el-col>
      <el-col :xs="10" :sm="3">이벤트</el-col>
    </el-row>
  </div>
</template>

<script>
export default {

}
</script>

<style>
.main-header {
  width: 100%;
  height: 70px;
  top: 0;
  text-align: center;
}

.title {
  margin-top: 10px;
  font-size: 28px;
  font-weight: 700;
  display: inline-block;
}

.header-icon {
  margin-top: 10px;
  font-size: 28px;
  color: black;
}

.el-icon-search {
  margin-right: 10px;
}

.main-menu {
  margin-bottom: 50px;
}

</style>