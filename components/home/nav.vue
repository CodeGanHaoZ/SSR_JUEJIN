<template>
  <nav class="view-nav">
    <div class="nav-list left" >
      <nuxt-link :to="{}" class="nav-item" v-for="item,index in this.navInfo" :key="index">
        <div class="category-popover-box">
          <span>
            {{ item.attributes.content }}
          </span>
        </div>
      </nuxt-link>
    </div>




  </nav>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return{
      navInfo:{
      }
    }
  },
  created(){
    this.asyncData()

  },
  methods:{
    // async...await
    async asyncData(){
    axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded'
    const url ='http://localhost:1337/api/classification-tabs?fields[0]=classification&fields[1]=content'
    try {
    const that = this
    const res = await axios.get(url)
    that.navInfo = res.data.data
    console.log(res);
    } catch (err) {
      console.log(err)
    }

  },
  }

}
</script>

<style scoped>
.view-nav {
    position: fixed;
    /* top: 5rem; */
    width: 100%;
    height: 3.833rem;
    z-index: 100;
    box-shadow: 0 1px 2px 0 rgb(0 0 0 / 5%);
    transition: all .2s;
    transform: translateZ(0);
    /* border: 1px solid; */
}

.view-nav .nav-list {
    max-width: 960px;
    height: 100%;
    margin: auto;
    display: flex;
    align-items: center;
    line-height: 1;
    /* border: 1px solid; */
}

.view-nav .nav-list .nav-item {
    height: 100%;
    align-items: center;
    display: flex;
    flex-shrink: 0;
    font-size: 16px;
    color: #71777c;
    padding: 0 16px;
    text-decoration: none;
}

@media (max-width: 980px){
  .view-nav .nav-list {
      width: auto;
      overflow-x: auto;
  }
}

/* @media (max-width: 980px){
  .view-nav .nav-list .nav-item:first-child, .view-nav .nav-list .nav-item:last-child {
      padding: 0 1.5rem;
  }
} */
</style>
