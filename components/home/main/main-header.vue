<template>
  <header class="list-header">
    <nav class="list-nav">
        <ul class="nav-list">
          <li class="nav-item"><nuxt-link :to="{}">推荐</nuxt-link></li>
          <li class="nav-item"><nuxt-link :to="{}">最新</nuxt-link></li>
          <li class="nav-item"><nuxt-link :to="{}">热榜</nuxt-link></li>
        </ul>
    </nav>
  </header>
</template>

<script>

</script>

<style scoped>
li{
  list-style: none;
}
a{
    text-decoration: none;
    color: #696d70;
}
.list-header{
    height: 50px;
    background-color: rgb(255,255,255);
}
.nav-list{
    float: left;
    margin:20px 0 0 15px;
}
.nav-item{
    float: left;
    padding: 0 13px;
    font-size: 14px;
    line-height: 13px;
    cursor: pointer;
}
.nav-list a:hover{
    color: #007fff;
}
.nav-item+.nav-item{
    border-left:1px solid rgb(231, 231, 231);
}
</style>
