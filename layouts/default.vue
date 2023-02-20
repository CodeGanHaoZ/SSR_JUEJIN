<template>
  <div>
    <Header />
    <Nav />
    <nuxt />
  </div>
</template>

<script>
import Header from '../components/home/header.vue'
import Nav from '../components/home/nav.vue'
export default {
   components:{
    Header,
    Nav
  }
}
</script>
