<template>
  <header class="list-header">
    <nav class="list-nav">
      <ul class="nav-list left">
        <li class="nav-item">
          <nuxt-link :to="{}">
            1
          </nuxt-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>

</script>

<style scoped>
.list-header {
  padding: 1.3rem 1rem;
  border-bottom: 1px solid hsla(0, 0%, 59.2%, .1);
}

.list-header .list-nav,
.list-header .nav-list {
  display: flex;
  justify-content: space-between;
}

.list-nav {
  justify-content: flex-start !important;
}
</style>
