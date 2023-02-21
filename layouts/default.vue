<template>
  <div>
    <Header />
    <Nav />
    <Main />
    <nuxt />
  </div>
</template>

<script>
import Header from '../components/home/header.vue'
import Nav from '../components/home/nav.vue'
import Main from '../components/home/main/main.vue'
export default {
   components:{
    Header,
    Nav,
    Main
  }
}
</script>
