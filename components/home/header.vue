<template>
  <!-- 页面顶部 -->
  <div class="main-header-box">
    <header class="main-header">
      <!-- 图标 -->
      <div class="logo">
        <img src="../../assets/images/logo.png" class="header-logo" alt="" />
      </div>
      <!-- 图标旁边列表 -->
      <div class="header-list">
        <ul>
          <li><a>首页</a></li>
          <li class="disappearSecond"><a>沸点</a></li>
          <li class="disappearSecond"><a>课程</a></li>
          <li class="disappearSecond"><a>直播</a></li>
          <li class="disappearSecond"><a>活动</a></li>
          <li class="disappearSecond"><a>商城</a></li>
          <li class="disappearFirst"><a>APP</a></li>
          <li class="disappearFirst"><a>插件</a></li>
        </ul>
      </div>
    </header>
  </div>
</template>

<script>
</script>

<style scoped>
/* header区域*/
.home_header {
  height: 68px;
  min-width: 600px;
  width: 100%;
  background-color: rgb(255, 255, 255);
}
.container {
  position: relative;
  margin: 0 auto;
  width: 100%;
  max-width: 960px;
}
/* 图标 */
.header_logo {
  float: left;
  margin: 22px 0 0 60px;
  cursor: pointer;
}

.header_logo {
  width: 106px;
}

/* 图标旁边列表 */
.header_list li {
  height: 43px;
  margin: 24px 0 0 25px;
  float: left;
  font-size: 0.9rem;
  cursor: pointer;
}

.header_list li:hover {
  border-bottom: 2px solid rgb(30, 143, 255);
  color: #696d70;
}
</style>
