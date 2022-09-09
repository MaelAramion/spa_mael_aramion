<template>
  <div class="home">
    <ArticleList msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import ArticleList from '@/components/ArticleList.vue'

export default {
  name: 'HomeView',
  components: {
    ArticleList
  }
}
</script>

<style>
.home{
  display: flex;

}
ArticleList{
  margin: auto;
}
</style>