<template>
  <aside>
    <div class="asideLi aside-first" style="transition: all .2s;">
      <div class="iconfont icon-shijian" id="good">
        <span class="title">{{ greeting }}</span>
        <div class="second-line">点亮你在社区的每一天</div>
      </div>
      <button id="goto">
        <span class="btn-text">去签到</span>
      </button>
    </div>

    <div class="asideLi-fixed asideLi">
      <template v-for="item, index in this.asideInfo">
        <div class="asideLi imgBox" v-if="index < 2" :key="index">
          <nuxt-link :to="{}">
            <img :src="`${baseUrl}` + item.attributes.advertisementCover.data.attributes.url" alt="error">
          </nuxt-link>
          <nuxt-link :to="{}" class="imgBox-advertisement">广告</nuxt-link>
          <div class="iconfont icon-RectangleCopy imgBox-eliminate"></div>
        </div>
      </template>

      <template v-for="item, index in this.asideInfo">
        <div class="asideLi aside-fourth" v-if="index == 2" :key="index">
          <img :src="`${baseUrl}` + item.attributes.advertisementCover.data.attributes.url" alt="error">
          <nuxt-link :to="{}" id="first">下载稀土掘金APP</nuxt-link>
          <nuxt-link :to="{}" id="second">一个帮助开发者成长的社区</nuxt-link>
        </div>
      </template>
    </div>

    <div class="asideLi aside-fifth">
      <div class="aside-fifth-li aside-fifth-firstLi user-block-header">
        <nuxt-link :to="{}" id="aside-fifth-author">🎖️作者榜</nuxt-link>
      </div>
      <template v-for="item,index in this.authorInfo" >
        <div class="aside-fifth-li aside-fifth-secondLi" :key="index">
          <div class="user-list">
            <div class="item">
              <nuxt-link :to="{}" id="aside-fifth-author" class="link">
                <img :src="`${baseUrl}` + item.attributes.authors.data[0].attributes.HeadCover.data.attributes.url"
                  alt="error" class="avatar">
                <div class="user-info">
                  <div class="username">
                    {{ item.attributes.authors.data[0].attributes.Name }}
                  </div>
                  <div class="position">
                    {{ item.attributes.authors.data[0].attributes.Signature }}
                  </div>
                </div>
              </nuxt-link>
            </div>
          </div>
        </div>
      </template>
      <div class="aside-fifth-li aside-fifth-thirdLi">
        <a href="https://juejin.cn/recommendation/authors/recommended">完整榜单</a>
        <!-- <nuxt-link :to="{}" class="iconfont icon-arrow-right"></nuxt-link> -->
      </div>
    </div>
  </aside>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      asideInfo: {
      },
      offsetY: "",
      baseUrl: "http://localhost:1337",
      authorInfo: {
      },
      greeting: ""
    }
  },
  created() {
    this.asyncData()
    this.greetingChange()
  },
  methods: {
    // async...await
    async asyncData() {
      axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded'
      const url1 = 'http://localhost:1337/api/advertisements?populate=*'
      try {
        const that = this
        const res = await axios.get(url1)
        that.asideInfo = res.data.data
        // console.log(that.asideInfo)
      } catch (err) {
        console.log(err)
      }
      const url2 = 'http://localhost:1337/api/author-lists?populate[0]=authors.HeadCover'
      try {
        const that = this
        const res = await axios.get(url2)
        that.authorInfo = res.data.data
        // console.log(that.authorInfo)
      } catch (err) {
        console.log(err)
      }

    },
    greetingChange() {
      let hours = new Date().getHours();
      if (hours >= 6 && hours <= 10) {
        this.greeting = '早上好'
      } else if (hours > 10 && hours <= 11) {
        this.greeting = '上午好'
      } else if (hours > 11 && hours <= 13) {
        this.greeting = '中午好'
      } else if (hours > 13 && hours <= 18) {
        this.greeting = '下午好'
      } else if (hours > 18 || hours <= 6) {
        this.greeting = '晚上好'
      }
      return this.greeting;
    }
  },
  mounted() {
    window.addEventListener("scroll", () => {
      this.offsetY =
        document.documentElement.scrollTop ||
        document.body.scrollTop ||
        window.pageYOffset
    })
  },
  watch: {
    offsetY(newValue, oldValue) {
      const asideLiFixedChange = document.querySelector('.asideLi-fixed')
      if (newValue >= 1000) {
        asideLiFixedChange.classList.add('asideLi-fixed-change')
        asideLiFixedChange.style.transition="all .2s"
      }
      else {
        asideLiFixedChange.classList.remove('asideLi-fixed-change')
        asideLiFixedChange.style.transition="all .2s"
      }
    }
  }
}
</script>

<style scoped>
a {
  text-decoration: none;
}

.asideLi {
  width: 240px;
  background-color: rgb(255, 255, 255);
  /* box-shadow: 0 0 1px 0 #cfd1d4; */
  /* box-shadow: 0 1px 2px 0 rgba(0,0,0,.05); */
}

.asideLi+.asideLi {
  margin-top: 15px;
  transition: all .2s;

}

.aside-first {
  position: relative;
  height: 104px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.aside-first #good {
  display: flex;
  flex-direction: column;

}

.aside-first #good .title {
  color: #1d2129;
  font-size: 16px;
  font-weight: 600;
  line-height: 24px;
}

.aside-first #good .second-line {
  color: #8a919f;
  font-size: 12px;
  font-weight: 400;
  line-height: 24px;
}

.aside-first #goto {
  border-radius: 4px;
  height: 36px;
  width: 74px;
  box-sizing: border-box;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  border: 1px solid rgba(30, 128, 255, .3);
  background-color: rgba(30, 128, 255, .05);
}

.aside-first #goto:hover {
  background-color: rgb(237, 245, 255);
}

#goto .btn-text {
  color: #1e80ff;
  font-size: 14px;
  font-weight: 400;
  white-space: nowrap;
}

.aside-first p {
  position: absolute;
  left: 50px;
  top: 65px;
  color: #4e5969;
  font-size: 14px;
  font-weight: 400;
}

.imgBox {
  position: relative;
  height: 199px;
  overflow: hidden;
  background-color: transparent;
  cursor: pointer;
}

.imgBox img {
  width: 240px;
}

.imgBox-advertisement {
  position: absolute;
  display: inline-block;
  right: 12px;
  top: 169px;
  padding: 2px 8px;
  font-size: 12px;
  color: rgb(253, 253, 254);
  border: 1px solid rgb(253, 253, 254);
  border-radius: 5px;
  background-color: rgba(161, 163, 165, 0.3);
}

.imgBox-eliminate {
  display: none;
  position: absolute;
  left: 218px;
  top: 2px;
  font-size: 22px !important;
  color: rgb(108, 108, 109);
}

.aside-fourth {
  position: relative;
  height: 80px;
  cursor: pointer;
}

.aside-fourth img {
  width: 50px;
  margin: 15px 0 15px 15px;
}

.aside-fourth #first {
  position: absolute;
  top: 19px;
  right: 46px;
  font-weight: 500;
  font-size: 14px;
  line-height: 22px;
  color: #1d2129;
}

.aside-fourth #second {
  position: absolute;
  top: 44px;
  right: 15px;
  font-size: 12px;
  line-height: 20px;
  color: #86909c;
}

.aside-fifth {
  background-color: transparent;
}

.aside-fifth .aside-fifth-li {
  background-color: rgb(255, 255, 255);
}

.aside-fifth-firstLi #aside-fifth-author {
  font-size: 14px;
  color: #333;
  padding: 1rem 1.3rem;
  /* border-bottom: 1px solid hsla(0, 0%, 59.2%, .1); */
}

.user-block-header {
  /* padding: 1rem 1.3rem; */
  border-bottom: 1px solid hsla(0, 0%, 59.2%, .1);
}

.icon-paihangbang {
  padding-left: 20px;
  margin-top: 10px;
  font-size: 28px;
  color: #1e80ff;
}

.aside-fifth-firstLi a {
  line-height: 45px;
  vertical-align: middle;
}

.aside-fifth-secondLi ul li {
  height: 70px;
  text-align: center;
  line-height: 70px;
  cursor: pointer;
}

.aside-fifth-secondLi:hover {
  background-color: rgb(247, 247, 247);
}

.aside-fifth-thirdLi {
  height: 45px;
  width: 240px;
  cursor: pointer;
}

.aside-fifth-thirdLi a {
  color: #007fff;
  font-size: 14px;
  line-height: 45px;
  font-weight: 400;
}

.aside-fifth-thirdLi a:nth-child(1) {
  padding-left: 87px;
}

.aside-sixth li {
  cursor: pointer;
}

.aside-sixth img {
  width: 35px;
  margin: 15px 0 15px 15px;
  vertical-align: middle;
}

.aside-sixth-smallA {
  color: #333;
  font-size: 14px;
  margin-left: 10px;
}

.aside-sixth li:hover {
  background-color: rgb(247, 247, 247);
}

.asideLi-fixed {
  background-color: rgb(244, 245, 245);

}

.asideLi-fixed-change {
  position: fixed;
  top: 55px;
  transition: all .2s;
}

aside {
  /* float: right; */
  position: absolute;
  right: 0px;
  top: 0;
  width: 240px;
  margin-left: 20px;
}

.item .position {
  color: #909090;
  font-size: 1rem;
  margin-bottom: 3px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.item .username {
  font-size: 14px;
  font-weight: 400;
  color: #333;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  margin-bottom: 3px;
}

.item .link .user-info {
  overflow: hidden;
}

.item .link .position {
  color: #909090;
  font-size: 12px;
  margin-bottom: 3px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.avatar {
  flex: 0 0 auto;
  width: 3.8rem;
  height: 3.8rem;
  border-radius: 50%;
  margin-right: .5rem;
}

.item .link {
  padding: 1rem 1.3rem;
  display: flex;
  align-items: center;
  cursor: pointer;
}
</style>
