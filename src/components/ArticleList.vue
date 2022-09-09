<template>
  <div class="articlelist">
    <h1 class="title">{{ title }}</h1>
    <div class="article" v-for="article in list" v-bind:key="article">
      <div class="article-title">
        <div class="article-title-fl"><div>{{ toUpperCase(article.title) }}</div></div>
        <h2>
          <router-link class="article-link" :to="{name: 'article', params: { id: article.id }}">{{ article.title }}</router-link>
        </h2>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'ArticleList',
  data: function(){
    return {
      title : 'Liste des articles',
      greeting : 'Hello',
      list: [],
      colors: ['#00a8ff', '#9c88ff', '#fbc531', '#4cd137', '#487eb0', '#0097e6', '#8c7ae6','#e1b12c','#44bd32','#40739e','#e84118','#7f8fa6','#273c75','#353b48','#c23616','#718093','#192a56','#2f3640']
    }
  },
  props: {
    msg: String,
    id: Number,
  },
  mounted () {
    axios
        .get('https://jsonplaceholder.typicode.com/posts')
        .then(response => (this.list = response.data))
  },
  methods: {
    randomColor: function(){
      const r = Math.floor(Math.random() * this.colors.length);

      return this.colors[r];
    },
    toUpperCase: function(title){
      return title.charAt(0).toUpperCase();
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.title{
  text-align: center;
}
.article{
  padding: 15px 0;
}
.articlelist{
  margin: auto;
}
.article-title{
  display: flex;
  align-items: center;
}
.article-title-fl{
  padding: 25px;
  color: white;
  background: brown;
  border-radius: 150000px;
  margin-right: 10px;
  width: 10px;
  height: 10px;
  line-height: 10px;
  text-align: center;
  font-size: 30px;
  position: relative;
}
.article-title-fl div{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
}
.article-link{
  text-decoration: none;
  color: white;
  text-align: center;
}
.article-link:hover{
  color: #273c75;
}
nav a{}
</style>
