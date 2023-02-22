<template>
  <main>
    <!-- 此盒子包含无限滚动列表和上方的导航栏（推荐|最新|热榜） -->
    <div class="main-box">
      <MainHeader />
      <!-- 无限滚动列表 -->
      <div class="entry-list-wrap">
        <div class="entry-list list">
          <li class="item">
            <div class="entry">
              <!-- 日期 -->
              <div class="meta-container">
                <a href="" class="user-message">ghw</a>
                <div class="date">
                  三天前
                </div>
                <div class="tag_list">
                  <nuxt-link :to="{}" class="tag">1</nuxt-link>
                </div>
              </div>
              <!-- 主体 -->
              <div class="content-wrapper" style="border-bottom: 1px solid rgba(228, 230, 235, 0.5);">
                <div class="content-main">
                  <!-- 文字1 -->
                  <div class="title-row">
                    1
                  </div>
                  <!-- 文字2 -->
                  <div class="abstract">
                    <a href=""></a>
                    <div></div>
                  </div>
                  <ul class="action-list jh-timeline-action-area">
                    <li class="item view">
                      <i></i>
                      <span>1</span>
                    </li>
                    <li class="item like">
                      <i></i>
                      <span>1</span>
                    </li>
                    <li class="item comment">
                      <i></i>
                      <span>1</span>
                    </li>
                  </ul>
                </div>
                <img src="" alt="" class="lazy thumb">
              </div>
            </div>
          </li>
        </div>
      </div>
    </div>
    <Aside />
  </main>
</template>

<script>
import MainHeader from './main-header';
import Aside from './aside';
export default {
  components: {
    MainHeader,
    Aside
  }
}
</script>

<style scoped>
.entry-list {
  width: 100%;
  background-color: #fff;
  position: relative;
}

.item {
  transition: all .3s ease-in;
}

.entry {
  cursor: pointer;
  position: relative;
  background: #fff;
  padding: 12px 20px 0;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.meta-container {
  color: #86909c;
}

.meta-container,
.meta-row {
  display: flex;
  align-items: center;
}

.meta-container .user-message {
  display: flex;
  align-items: center;
  margin-right: 8px;
  max-width: 162px;
  font-size: 13px;
  line-height: 22px;
  color: #4e5969;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  word-break: break-all;
}

.meta-container .date {
  position: relative;
  padding: 0 10px;
  line-height: 22px;
  font-size: 13px;
  flex-shrink: 0;
}

.tag_list .tag,
.tag_list {
  display: flex;
  align-items: center;
}

.tag_list .tag {
  position: relative;
  flex-shrink: 0;
  font-size: 13px;
  line-height: 22px;
  padding: 0 8px;
  color: #86909c;
}

.content-wrapper {
  display: flex;
  padding-bottom: 12px;
  border-bottom: 1px solid #e5e6eb;
  margin-top: 10px;
  width: 100%;
}

.content-wrapper .content-main {
  flex: 1 1 auto;
}

.title-row {
  display: flex;
  margin-bottom: 8px;
}

.title {
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  color: #1d2129;
  width: 100%;
  display: -webkit-box;
  overflow: hidden;
  text-overflow: ellipsis;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 1;
}

.abstract {
  margin-bottom: 10px;
}

.abstract a {
  color: #86909c;
  font-size: 13px;
  line-height: 22px;
  display: -webkit-box;
  overflow: hidden;
  text-overflow: ellipsis;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 1;
}

.action-list>.item,
.action-list {
  display: flex;
  align-items: center;
}

ul {
  padding: 0;
  margin: 0;
}

.action-list>.item {
  position: relative;
  margin-right: 20px;
  font-size: 13px;
  line-height: 20px;
  color: #4e5969;
  flex-shrink: 0;
}

.action-list>.item,
.action-list {
  display: flex;
  align-items: center;
}

li {
  list-style: none;
}

.action-list>.item.view i {
  background-image: url(//lf3-cdn-tos.bytescm.com/obj/static/xitu_juejin_web/img/view.1eda8fa.png);
}

.action-list>.item i {
  display: block;
  width: 16px;
  height: 16px;
  background-size: 100%;
}

.action-list>.item span {
  margin-left: 4px;
}

.action-list>.item {
  position: relative;
  margin-right: 20px;
  font-size: 13px;
  line-height: 20px;
  color: #4e5969;
  flex-shrink: 0;
}

.action-list>.item,
.action-list {
  display: flex;
  align-items: center;
}

.action-list>.item.like i {
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAACXBIWXMAABYlAAAWJQFJUiTwAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAJ9SURBVHgB7VZNbtNQEP7GP7AkN8DcoJyA5gRNTwCR2kqsUm9YEKEaoZRl0hUSBLWcAHOCpjdIT1AfIewgTjzM+AccxwHXLRYS/STnvbyxZ743b34e8L+DcEMMhu+fERk7DLTAuAwRjjz3eVD1+xsROD75eARmr7AczDlsVyVhoCbeDt85mXHmqLtkbst0Ko9jk31aVU9tAgvYW7FxYNJ3D85eufuTOZtKYiZu3X4z/LBdRU9tAia4E0+YL7I1z+3OmPEpkWOrip7aBED0RAcb7K8KeBb/alD+LQIa+TI48kxfuAfTVSlVMlybgAafpN1RYgujopwIOzpGEhuogGuloTc8bd2j5TmS8/VfHu7t5uUaeCaRygORPaqi00JFJAVn2UuNa667xXfEeJZ+rePR+Kool7gIQg67+RpBJTvo5QMoZHPXxFLW8Tld2lhoUqMOfg/JlKjdT2Pnpwf0bDlx3worG1EnPlENF0m5OayO5+7NyjRLHXgMfCsNQhumrBviRfRAhnqyu0KAYXmpcX/BfKKekL+dvBIheOUddkuNK7QO6A43ycXDvolYr5OtGTnlD3VU41rVZLdfccvIipMYDdYINAHZZJyicgR+4wQ0hbVH6Px7RBeNE9BM0lGbVxorTRNImhcxf8mvNxcDafOywBM0TUCqqEa/I09QbF6NECDQdjKuN6hGCJSlX2MENqXfGgFKS6hlmA9wi7hvLJ/qWEy/DL96AfMlEXWkU/mD0XiCkjud7kRk56iOltwRYz3ShM7KXlhpx4PheBR3qxzS6zbSi0YtyOZe9919D38ioNC2vIDl6NyQC2bWtzWVomvf93gWwg7KXH+HfwY/AGsn+Lf3Dim6AAAAAElFTkSuQmCC);
}

.action-list>.item.comment i {
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAACXBIWXMAABYlAAAWJQFJUiTwAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAKRSURBVHgB7VZNbtpQEJ55BlR15RvUOUHTG5ATJD1BQ9NU6gq8JKiKoyrJ0u2qUmkFOUGaE5TegJwg7gnqLRh7MvMwwiDbYHCUDZ9kHph5M9+bN38AO+zwzEAoiEv3xz4v/KAFiK/0S6J/qPCBoui+Y38cFlC3HgHH7Zk1FTXZUIt/mivEPVY6GFFw4difPNiWwNW3X+dLhj1iA3JqProXq7EQ8TVoz4A1147OWfPkAjYhcO1+twirt7FSEexPiG4+26cDyMEXt1s3AI7Z+LsZ4TEFB1newBzjf2B6Gi8kaqwyvEpHFgmVtjmxcTgm401R44I2G0M2KjpEV5W9KbG0koC+8znrt47d8GFDCAk+gJCQwNyvwqS1LLNwBbHbHuQ7G99bJ4rXgY4LRPGqz4T2koda8EAERl2zIrory7hArlBnDmdSDSbHyf8WrwDVNHKV0YOyQdGNXhAPMwlgnHKjaHQPJUNBOEjamL9fhI7SMt0/Q3uu08wjoJGWLk+FZQKefLyEwIKSETcxwTCbANFfWQLAIygZCFifrjkEQq73WgixCaUziHWi+p1JIC65Hj/mpdt1oCQkq2u7+f4uk4BAGo8minguFQy2hFRXvlonqTuXgK5aRLqHc/m8vXK7LdgCE6hYskolTGtqqWnYsU+dmITJrnCvv/7sOXKSDVCBiScrJgeVBHInIokDuYqEsB5KQqgMl7uk1A4DwrpCkFLLExL0x1HAWfXCr2H4X2TOWh+wEAGB7pBQcRITzgwymvmxEilcVtp+cX1cfs20Drv2VKyDSVUPI4Ij3lRPEfFJclzXEvIQlXhioZ4QYaNjn/Q3IrAMiQmDA0wB+QGEflr/ENK6xXOXFS8QRQdFx/YdnhyP1D0hcwr1KvEAAAAASUVORK5CYII=);
}

.thumb {
  flex: 0 0 auto;
  width: 120px;
  height: 80px;
  margin-left: 24px;
  background-color: #fff;
  border-radius: 2px;
}

.lazy {
  position: relative;
  -o-object-fit: cover;
  object-fit: cover;
}

img {
  border-style: none;
}

a {
  text-decoration: none;
  cursor: pointer;
  color: #909090;
}

main {
  width: 1000px;
  height: 3000px;
  margin: 120px auto;
}

.main-box {
  float: left;
  width: 740px;
}</style>
