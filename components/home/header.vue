<template>
  <div class="main-header-box">
    <header class="main-header">
      <div class="container">
        <nuxt-link :to="{ name: 'index' }" class="logo">
          <img src="../../assets/images/logo.png" class="logo-img" alt="" />
        </nuxt-link>

        <nav class="main-nav">
          <ul class="nav-list">
            <li><nuxt-link :to="{name:'index'}" class="nav-item">首页</nuxt-link></li>
            <li><nuxt-link :to="{name:'index'}" class="nav-item">沸点</nuxt-link></li>
            <li><nuxt-link :to="{name:'index'}" class="nav-item">课程</nuxt-link></li>
            <li><nuxt-link :to="{name:'index'}" class="nav-item">直播</nuxt-link></li>
            <li><nuxt-link :to="{name:'index'}" class="nav-item">活动</nuxt-link></li>
            <li><nuxt-link :to="{name:'index'}" class="nav-item">商城</nuxt-link></li>
            <li><nuxt-link :to="{name:'index'}" class="nav-item">APP</nuxt-link></li>
            <li><nuxt-link :to="{name:'index'}" class="nav-item">插件</nuxt-link></li>
          </ul>
        </nav>
      </div>
      <!-- <div class="header-list"></div> -->
    </header>
  </div>
</template>

<script>
</script>

<style scoped>
/* header区域*/
.main-header-box {
  position: relative;
  height: 5rem;
}

.main-header.visible {
  transform: translateZ(0);
}

.main-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  transition: all 0.2s;
  /* transform: translate3d(0,-100%,0); */
}

.main-header .container {
  margin: auto;
  max-width: 1440px;
  /* border: 1px solid; */
}

.container {
  display: flex;
  align-items: center;
  height: 100%;
}

.container {
  position: relative;
  margin: 0 auto;
  width: 100%;
  max-width: 960px;
}

/* .container {
    position: relative;
    margin: 0 auto;
    width: 100%;
    max-width: 960px;
} */
.logo {
  margin-right: 1rem;
  margin-left: 24px;
  display: inline-block;
  height: 22px;
  width: auto;
}

.logo-img {
  display: block;
  width: 137px;
  height: 28px;
}

.nav-list {
  display: flex;
  align-items: center;
  justify-content: space-between;
  position: relative;
  /* flex-direction: row-reverse; */
  height: 100%;
  margin: 0;
}

.nav-item {
  color: #000000;
  text-decoration: none;
}
li{
  list-style: none;

}
</style>
