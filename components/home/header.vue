<template>
  <div class="main-header-box">
    <header class="main-header">
      <div class="container">
        <nuxt-link :to="{ name: 'index' }" class="logo">
          <img src="../../assets/images/logo.png" class="logo-img" alt="" />
        </nuxt-link>
        <nav class="main-nav">
          <ul class="nav-list">
            <li v-for="item,index in this.tabInfo" :key="index" class="nav-item">
              <nuxt-link :to="{name:'index'}" class="link">
                {{ item.attributes.content }}
                <span class="tablead" v-if="item.attributes.tagState==1">{{ item.attributes.tag }}</span>
              </nuxt-link>
            </li>
          </ul>
          <client-only>
            <el-dropdown trigger="click" >
              <span class="el-dropdown-link">
                首页<i class="el-icon-arrow-down el-icon--right"></i>
              </span>
              <el-dropdown-menu slot="dropdown"  class="phone-nav-list" :append-to-body="false">
                <el-dropdown-item v-for="item,index in this.tabInfo" :key="index" class="phone-nav-item">
                  <nuxt-link :to="{name:'index'}" class="phone-link">
                    {{ item.attributes.content }}
                    <span class="phone-tablead" v-if="item.attributes.tagState==1">{{ item.attributes.tag }}</span>
                  </nuxt-link>
                </el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
          </client-only>
        </nav>
      </div>
    </header>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return{
      tabInfo:{
      },
      offsetY:""
    }
  },
  created(){
    this.asyncData()

  },
  methods:{
    // async...await
    async asyncData(){
    axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded'
    const url ='http://localhost:1337/api/top-tabs?fields[0]=classification&fields[1]=content&fields[2]=tagState&fields[3]=tag'
    try {
      const that = this
      const res = await axios.get(url)
      that.tabInfo = res.data.data
      // console.log(res);
    } catch (err) {
      console.log(err)
    }
  }

  },
  mounted(){
      window.addEventListener("scroll", () => {
        this.offsetY =
        document.documentElement.scrollTop ||
        document.body.scrollTop ||
        window.pageYOffset;
        if (this.scrollY >= 500) {
          console.log(this.scrollY)

      }
    })
  },
  watch: {

    offsetY(newValue, oldValue) {
      const main_header = document.querySelector('.main-header');
      const view_nav  = document.querySelector('.view-nav ');
      if (newValue >= 500) {

        main_header.style.transform = 'translate3d(0,-100%,0)';
        view_nav.style.transform = 'translate3d(0,-60px,0)';
      }
      else{
        main_header.style.transform = 'none';
        view_nav.style.transform = 'none';
      }
    }
  }
}
</script>

<style scoped>
.main-header.visible {
    transform: translateZ(0);
}
.main-header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    transition: all .2s;
    /* transform: translate3d(0,-100%,0); */
}
.main-header {
    border-bottom: 1px solid #f1f1f1;
    color: #909090;
    height: 60px;
    z-index: 250;
    background-color: #ffffff;
}
.main-header .container {
  margin: auto;
  max-width: 1440px;
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
  margin-right: 10px;
  margin-left: 18px;
  display: inline-block;
  /* height: 22px; */
  width: auto;
  /* border: 1px solid; */
}
.logo-img{
  width:107px;
  /* height:30px; */
}
.main-nav{
  font-size: 14px;
  height: 60px;
}
.nav-list {
  height: 100%;
  display: flex;
  align-items: center;
}
.nav-item {
  position: relative;
  display: flex;
  /* border: 1px solid; */
  width: 56px;
  line-height: 62px;
  justify-content: center;
}
li{
  list-style: none;
}
.link{
  color: #696d70;
  text-decoration: none;
  display: inline-block;
  height: 60px;
  border-bottom: 2px solid transparent;

}
.el-dropdown-menu__item:focus, .el-dropdown-menu__item:not(.is-disabled):hover{
    background: none !important;
}
.el-dropdown{
  width: 50px;
  position: absolute;
  top: 20px;
  left: 149px;
  display: none;
}
.el-dropdown-link{
  color: #1e80ff;
}
.el-dropdown-menu{
  width: 150px !important;
  height: 340px !important;
  top: 86px;
}
.el-popper >>> .popper__arrow {
    border-bottom-color: #1EBEF4 !important;
    left: 50% !important;
    visibility: hidden;
}
.phone-nav-list {
  left: 88px !important;
  top: 38px !important;
}
.phone-nav-item {
  position: relative;
  display: flex;
  justify-content: center;
}

.link:hover{
  background-color: none;
  border-bottom: 2px solid #1e80ff;
  color: #000;
}
.phone-link{
  color: #696d70;
  text-decoration: none;
  border-bottom: 2px solid transparent;
}
.phone-link:hover{
  border-bottom: 2px solid #1e80ff;
  color: #000;
}
.phone-tablead{
  position: absolute;
  bottom: 20px;
  right: 4px;
  z-index: 99;
  white-space: nowrap;
  padding: 2px 7px;
  background-color: #ee502f;
  border-radius: 50px;
  text-align: center;
  font-weight: 500;
  font-size: 16px;
  transform: scale(.5);
  line-height: 18px;
  color: #fff;
}
.tablead{
  position: absolute;
  top: 5px;
  left: 24px;
  z-index: 99;
  white-space: nowrap;
  padding: 2px 7px;
  background-color: #ee502f;
  border-radius: 50px;
  text-align: center;
  font-weight: 500;
  font-size: 16px;
  transform: scale(.5);
  line-height: 18px;
  color: #fff;
}
@media screen and (max-width: 1300px) {
    .nav-list {
        display: none !important;
    }
    .el-dropdown{
      display: block !important;
    }
    /* .phone-nav-list {
      left: -62px !important;
      top: 18px !important;
    } */
}
</style>
