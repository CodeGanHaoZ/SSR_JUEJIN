<template><!-- <main class="container main-container with-view-nav">
    <div class="view timeline-index-view">
      <div class="timeline-container">
        <div class="timeline-content">
          <div class="timeline-entry-list">
            <div class="entry-list-container">
              <div class="entry-list-wrap">
                1
              </div>
            </div>
          </div>

        </div>
      </div>
    </div>
</main> -->
  <main>
    <!-- 此盒子包含无限滚动列表和上方的导航栏（推荐|最新|热榜） -->
    <div class="main-box">
      <MainHeader />
      <!-- 无限滚动列表 -->
      <ul class="main-ul">
        <!-- 置顶的li -->
        <li class="main-ul-li">
          <ul class="main-ul-li-header">
            <li class="userName">掘金酱</li>
            <li class="releaseDate">29天前</li>
          </ul>
          <a>
            <h3 class="title">8月更文活动倒计时！</h3>
            <p class="article-first">
              在这个热情的8月，「掘金·日新计划」再次起航，超多创作奖励等你来拿！
            </p>
            <div class="cover">
              <img src="image/gwtz.webp" alt="">
            </div>
            <div></div>
          </a>
        </li>
        <!-- 其他li -->
        <!-- 定义模板 -->
        <div class="templateBox">
          <li class="main-ul-li">
            <ul class="main-ul-li-header">
              <li class="userName">{{ userName }}</li>
              <li class="releaseDate">{{ releaseDate }}</li>
              <li class="label">{{ label }}</li>
            </ul>
            <a>
              <h3 class="title">{{ title }}</h3>
              <p class="article">{{ article }}</p>
              <div class="cover">
                <img src="image/gwtz.webp" alt="">
              </div>
            </a>
            <ul class="main-ul-li-footer">
              <li>
                <div class="iconfont icon-browse"></div>&nbsp<a>1000</a>
              </li>
              <li>
                <div class="iconfont icon-good"></div>&nbsp<a>100</a>
              </li>
              <li>
                <div class="iconfont icon-comment"></div>&nbsp<a>10</a>
              </li>
            </ul>
            <div class="iconfont icon-close main-ul-li-footer-close"></div>
          </li>
        </div>
      </ul>
    </div>
    <Aside />
  </main>
</template>

<script>
import MainHeader from './main-header';
import Aside from './aside';
export default {
   components:{
      MainHeader,
      Aside
  }
}
</script>

<style scoped>
/* .container {
  position: relative;
  margin: 0 auto;
  width: 100%;
  max-width: 960px;
  border: 1px solid;
}

.container .view.timeline-index-view {
  margin-top: 93px;
}

.timeline-content {
  position: relative;
  margin-top: .33rem;
}

.timeline-entry-list {
  margin-right: 21.667rem;
  border-radius: 2px;
  width: 700px;
} */

/* 页面主体内容区整体布局 */

li{
    list-style-type: none;
}
a{
    text-decoration: none;
    color: #696d70;
}
main{
    width: 1000px;
    height: 3000px;
    margin: 120px auto;
}
.main-box{
    float: left;
    width: 740px;
}

.main-ul{
    margin-top: 2px;
    background-color: rgb(255,255,255);
}


/* 置顶li样式 */
.article-first {
    display: block;
    float: left;
    width: 78%;
    height: 50px;
    margin-top: 10px;
    border: 0px;
    line-height: 25px;
    font-size: 13px;
    overflow: hidden;
    text-overflow: ellipsis;
}

/* 模板样式 */
.templateBox {
    position: relative;
    width: 100%;
    height: 138px;
}

.templateBox:hover {
    background-color: rgb(249, 249, 249);
}

.main-ul-li {
    width: 95%;
    height: 138px;
    margin: 0 18px;
    border-bottom: 2px solid rgb(244, 245, 245);
    cursor: pointer;
}

.main-ul-li-header {
    width: 100%;
    height: 41px;
    margin-left: -10px;
}

.main-ul-li-header li {
    float: left;
    padding: 0 10px;
    margin: 12px 0;
    font-size: 13px;
}

.main-ul-li-header li:nth-child(1):hover {
    color: rgb(30, 143, 255);
}

.main-ul-li-header li+li {
    border-left: 2px solid rgb(231, 231, 231);
}

.title {
    display: block;
    float: left;
    width: 78%;
    font-size: 17px;
    white-space: hidden;
    overflow: hidden;
    text-overflow: ellipsis;
}

.article {
    display: block;
    float: left;
    width: 78%;
    height: 25px;
    margin-top: 10px;
    border: 0px;
    line-height: 25px;
    font-size: 13px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.cover img {
    float: right;
    height: 82px;
    margin: -18px 0;
}

.main-ul-li-footer {
    float: left;
    width: 78%;
    height: 20px;
    margin-left: -10px;
}

.main-ul-li-footer li {
    float: left;
    padding: 10px;
}

.main-ul-li-footer li+li:hover {
    color: rgb(30, 143, 255);
}

.main-ul-li-footer li .iconfont {
    float: left;
    margin-top: 3px;
    font-size: 18px;
}

.main-ul-li-footer li a {
    font-size: 13px;
}

.main-ul-li-footer-close {
    position: absolute;
    top: 13px;
    right: 16px;
    color: #bababa;
}

.main-ul-li-footer-close:hover {
    color: rgb(30, 143, 255);
    font-weight: bold;
}

/* 回到顶部按钮 */
.toTop {
    display: none;
    position: fixed;
    right: 20px;
    bottom: 50px;
    width: 40px;
    height: 40px;
    border-radius: 20px;
    background-color: rgb(255, 255, 255);
    box-shadow: 0 0 20px 0 #cfd1d4;
    font-size: 28px;
    text-align: center;
    line-height: 40px;
    cursor: pointer;
}

.toTopTips {
    position: fixed;
    display: none;
    position: fixed;
    right: 56px;
    bottom: 87px;
    width: 60px;
    height: 20px;
    border: 1px solid rgb(33, 32, 32);
    color: rgb(33, 32, 32);
    font-size: 12px;
    text-align: center;
    line-height: 20px;
}
</style>
