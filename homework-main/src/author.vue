<template>
  <div>
    <Nav />
    <AuthorHeader />
    <div class="container">
      <main>
        <AuthorInformation />
        <AuthorBasic />
      </main>
    </div>
  </div>
</template>

<script setup>
import Nav from './components/Nav.vue'
import AuthorHeader from './components/author_com/header.vue'
import AuthorInformation from './components/author_com/information.vue'
import AuthorBasic from './components/author_com/basic.vue'
import './components/author_com/author.css'
</script>
<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}
main {
  padding: 20px 0;
}
</style>