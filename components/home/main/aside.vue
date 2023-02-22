<template>
  <aside>
      <ul>
        <li class="asideLi aside-first">
          <div class="iconfont icon-shijian" id="good"></div>
          <div id="goto">去签到</div>
          <p>点亮你在社区的每一天</p>
        </li>
        <div class="asideLi-fixed asideLi">
          <li class="asideLi imgBox">
            <a>
              <img src="image/kfzdh.webp" alt="">
            </a>
            <a class="imgBox-advertisement">广告</a>
            <div class="iconfont icon-RectangleCopy imgBox-eliminate"></div>
          </li>
          <li class="asideLi imgBox">
            <a>
              <img src="image/ydtz.webp" alt="">
            </a>
            <a class="imgBox-advertisement">广告</a>
            <div class="iconfont icon-RectangleCopy imgBox-eliminate"></div>
          </li>
          <li class="asideLi aside-fourth">
            <img src="image/erweima.png" alt="">
            <a id="first">下载稀土掘金APP</a>
            <a id="second">一个帮助开发者成长的社区</a>
          </li>
        </div>
        <li class="asideLi aside-fifth">
          <ul>
            <li class="aside-fifth-li aside-fifth-firstLi">
              <a class="iconfont icon-paihangbang"></a>
              <a id="aside-fifth-author">作者榜</a>
            </li>
            <li class="aside-fifth-li aside-fifth-secondLi">
              <ul>
                <li>欧西里斯之天空龙</li>
                <li>欧贝利斯克之巨神兵</li>
                <li>拉之翼神龙</li>
              </ul>
            </li>
            <li class="aside-fifth-li aside-fifth-thirdLi">
              <a>完整榜单</a>
              <a class="iconfont icon-arrow-right"></a>
            </li>
          </ul>
        </li>
        <li class="asideLi aside-sixth">
          <ul>
            <li>
              <a>
                <img src="image/manyouzhinan.png" alt="">
                <a class="aside-sixth-smallA">稀土掘金漫游指南</a>
              </a>
            </li>
            <li>
              <a>
                <img src="image/liulanqichajian.png" alt="">
                <a class="aside-sixth-smallA">安装掘金浏览器插件</a>
              </a>
            </li>
            <li>
              <a>
                <img src="image/fanyijihua.png" alt="">
                <a class="aside-sixth-smallA">前往掘金翻译计划</a>
              </a>
            </li>
          </ul>
        </li>
      </ul>
    </aside>
</template>

<script>

</script>

<style scoped>
/* 侧边栏样式 */
.asideLi{
    width: 240px;
    background-color: rgb(255,255,255);
    box-shadow: 0 0 1px 0 #cfd1d4;
}

.asideLi+.asideLi{
    margin-top: 15px;
}

/* 第一个li */
.aside-first{
    position: relative;
    height: 104px;
}
.aside-first #good{
    float: left;
    margin: 20px 0 0 33px;
    color: #1d2129;
    font-size: 18px;
    font-weight: 500;
}
.aside-first #goto{
    float: right;
    width: 68px;
    height: 30px;
    line-height: 30px;
    text-align: center;
    margin: 16px 23px 0 0;
    border: 1px solid #1e80ff;
    border-radius: 20px;
    color: #1e80ff;
    font-size: 14px;
    font-weight: 400;
    cursor: pointer;
}
.aside-first #goto:hover{
    background-color: rgb(237,245,255);
}
.aside-first p{
    position: absolute;
    left: 50px;
    top: 65px;
    color: #4e5969;
    font-size: 14px;
    font-weight: 400;
}

/* 第二，三个li */
.imgBox{
    position: relative;
    height: 199px;
    overflow: hidden;
    background-color: transparent;
    cursor: pointer;
}
.imgBox img{
    width: 240px;
}
.imgBox-advertisement{
    position: absolute;
    display: inline-block;
    right: 12px;
    top: 169px;
    padding:2px 8px;
    font-size: 12px;
    color: rgb(253, 253, 254);
    border:1px solid rgb(253, 253, 254);
    border-radius: 5px;
    background-color:rgba(161, 163, 165, 0.3);
}
.imgBox-eliminate{
    display: none;
    position: absolute;
    left: 218px;
    top: 2px;
    font-size: 22px !important;
    color: rgb(108, 108, 109);
}

/* 第四个li */
.aside-fourth{
    position: relative;
    height: 80px;
    cursor: pointer;
}
.aside-fourth img{
    width: 50px;
    margin: 15px 0 15px 15px;
}
.aside-fourth #first{
    position: absolute;
    top: 19px;
    right: 46px;
    font-weight: 500;
    font-size: 14px;
    line-height: 22px;
    color: #1d2129;
}
.aside-fourth #second{
    position: absolute;
    top: 44px;
    right: 15px;
    font-size: 12px;
    line-height: 20px;
    color: #86909c;
}

/* 第五个li */
.aside-fifth{
    background-color: transparent;
}
.aside-fifth .aside-fifth-li{
    margin-top: 1px;
    background-color: rgb(255,255,255);
}
.aside-fifth-firstLi #aside-fifth-author{
    font-size: 14px;
    color: #333;
}
.icon-paihangbang{
    padding-left:20px;
    margin-top: 10px;
    font-size: 28px;
    color: #1e80ff;
}
.aside-fifth-firstLi a{
    line-height: 45px;
    vertical-align: middle;
}
.aside-fifth-secondLi ul li{
    height: 70px;
    text-align: center;
    line-height: 70px;
    cursor: pointer;
}
.aside-fifth-secondLi ul li:hover{
    background-color: rgb(247, 247, 247);
}
.aside-fifth-thirdLi{
    height: 45px;
    width: 240px;
    cursor: pointer;
}
.aside-fifth-thirdLi a{
    color: #007fff;
    font-size: 14px;
    line-height: 45px;
    font-weight: 400;
}
.aside-fifth-thirdLi a:nth-child(1){
    padding-left: 87px;
}

/* 第六个li */
.aside-sixth li{
    cursor: pointer;
}
.aside-sixth img{
    width: 35px;
    margin: 15px 0 15px 15px;
    vertical-align: middle;
}
.aside-sixth-smallA{
    color: #333;
    font-size: 14px;
    margin-left: 10px;
}
.aside-sixth li:hover{
    background-color: rgb(247, 247, 247);
}

/* 响应式 */
.asideLi-fixed{
    background-color: rgb(244,245,245);
}
.asideLi-fixed-change{
    position: fixed;
    top: 55px;
}

aside{
    float: right;
    width: 240px;
    margin-left: 20px;
}

@media screen and (max-width:1000px){
    .asideLi{display: none;}
    main{width: 100%;}
    .main-box{width: 100%;}
}
</style>
